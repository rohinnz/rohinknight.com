---
layout: post
title:  "[OLD] Component Based Game Development"
date:   2011-01-10 17:00:00 +1300
categories: gamedev
---
**This post is from my old website. Some information may no longer be relevant.**

I recently learnt about component based game engines at [http://cowboyprogramming.com/2007/01/05/evolve-your-heirachy/](http://cowboyprogramming.com/2007/01/05/evolve-your-heirachy/). But I was unsure how I should implement it.

After playing around and looking at how other people had done it, this is what I ended up with.

First I created an entity type which I could attach components too. It has a name for identification, a boolean variable to tell the Entity Manager whether it is still breathing, and 3 containers for the components. The first container is a dictionary of all attached components, the component name for the dictionary key. The second is just a list of components that need to be updated and in what order, and the third is a list of components that are actively listening to messages being sent from other components.

```python
class Entity(object):
    def __init__(self, name):
        self.name = name
        self.alive = True
        self.components = {}
        self.component_update_order = None
        self.message_listeners = []
```

Next I created the components. Each component is a subclass of Component, and it passes its type, entity reference and whether it wants to listen to messages to the superclass.

```python
class Component(object):
    def __init__(self, type, entity, register_as_listener = False):
        self.entity = entity
        entity.components[type] = self
        if register_as_listener:
            entity.message_listeners.append(self)
 
    def update(self):
        pass
 
    def handle_message(self, m_sender, m_type, m_data):
        pass
 
    def post_message(self, m_sender, m_type, m_data = None):
        for component in self.entity.message_listeners:
            component.handle_message(m_sender, m_type, m_data)
 
class SizeCom(Component):
    def __init__(self, entity, w, h):
        super(SizeCom, self).__init__('size', entity)
        self.w = w
        self.h = h
 
class PositionCom(Component):
    def __init__(self, entity, x, y):
        super(PositionCom, self).__init__('position', entity)
        self.x = x
        self.y = y
 
class MovementCom(Component):
    def __init__(self, entity, dx, dy):
        super(MovementCom, self).__init__('movement', entity)
        self.positionCom = entity.components['position']
        self.dx = dx
        self.dy = dy
 
    def update(self):
        self.positionCom.x += self.dx
        self.positionCom.y += self.dy
 
class GravityCom(Component):
    def __init__(self, entity):
        super(GravityCom, self).__init__('gravity', entity)
        self.movementCom = entity.components['movement']
 
    def update(self):
        self.movementCom.dy += GRAVITY_SPEED
 
class CollisionCom(Component):
    def __init__(self, entity):
        super(CollisionCom, self).__init__('collision', entity)
        self.positionCom = entity.components['position']
        self.sizeCom = entity.components['size']
        self.movementCom = entity.components['movement']
 
    def update(self):
 
        # ... check for collision ...
 
        if ground_collision:
 
            self.positionCom.y = 0
            self.movementCom.dy = 0
 
            self.post_message(self, M_GROUND_COLLISION, collision_point)
 
class AlwaysJumpingCom(Component):
    def __init__(self, entity, True):
        super(CollisionCom, self).__init__('always jumping', entity, True)
        self.movementCom = entity.components['movement']
 
    def handle_message(self, m_sender, m_type, m_data):
        if m_type == M_GROUND_COLLISION:
            self.movementCom.dy -= 20    # Time to jump in the air!
```

As you can see, the Always Jumping component waits for feedback of a collision using the message handler. The message handler is a great way for components to pass messages to each other without having to check if a component exists.

Next I used a factory pattern for building each object. First a new entity is created with a name, and then each component is created and attaches itself to the entity.

Then we add a component update order (if any) and attach it to the entity manager.

```python
class Factory(object):
    @classmethod
    def build_object_with_only_position_info(cls, xpos, ypos):
        entity = Entity('object with only position info')
 
        p = PositionCom(entity, xpos, ypos)
 
        EntityManager.add_entity(entity)
        return entity
 
    @classmethod
    def build_platform(cls, width, height, xpos, ypos):
        entity = Entity('platform')
 
        p = PositionCom(entity, xpos, ypos)
        s = SizeCom(entity, width, height)
 
        EntityManager.add_entity(entity)
        return entity
 
    @classmethod
    def build_monster(cls, xpos, ypos, width, height):
        entity = Entity('monster')
 
        p = PositionCom(entity, xpos, ypos)
        s = SizeCom(entity, width, height)
        a = AIMovementCom(entity)
        g = GravityCom(entity)
        c = CollisionApplyClippingCom(entity)
 
        entity.component_update_order = (a, g, c)
        EntityManager.add_entity(entity)
        return entity
 
    @classmethod
    def build_player(cls, xpos, ypos):
        entity = Entity('player')
 
        WIDTH = 30
        HEIGHT = 60
 
        p = PositionCom(entity, xpos, ypos)
        s = SizeCom(entity, WIDTH, HEIGHT)
        m = PlayerMovementCom(entity)
        g = GravityCom(entity)
        c = CollisionApplyClippingCom(entity)
 
        entity.component_update_order = (m, g, c)
        EntityManager.add_entity(entity)
        return entity
 
    @classmethod
    def build_bullet(cls, xpos, ypos, dx):
        entity = Entity('bullet')
 
        WIDTH = 10
        HEIGHT = 4
 
        p = PositionCom(entity, xpos, ypos)
        s = SizeCom(entity, WIDTH, HEIGHT)
        m = MovementCom(entity, dx, 0)
        d = DestroyWhenOutsideCamCom(entity)
        c = CollisionDestroyMonsterCom(entity)
 
        entity.component_update_order = (m, d, c)
        EntityManager.add_entity(entity)
        return entity
 
    @classmethod
    def build_deadly_bouncing_ball(cls, xpos, ypos):
        entity = Entity('deadly bouncing ball')
 
        WIDTH = 10
        HEIGHT = 10
 
        p = PositionCom(entity, xpos, ypos)
        s = SizeCom(entity, WIDTH, HEIGHT)
        m = MovementCom(entity, 0, 0)
        g = GravityCom(entity)
        j = AlwaysJumpingCom(entity)
 
        entity.component_update_order = (m, g, j)
        EntityManager.add_entity(entity)
        return entity
```

And here is the Entity Manager. During every update, the entity manager will call each entity’s components in the order specified.

```python
class EntityManager(object):
    entities = []
    updateable_entites = []
 
    @classmethod
    def add_entity(cls, entity):
        cls.entities.append(entity)
 
        if entity.component_update_order != None:
            cls.updateable_entites.append(entity)
 
        EventManager.post_event(ET_ENTITY, E_NEW_ENTITY, entity)
 
    @classmethod
    def remove_entity(cls, entity):
        cls.entities.remove(entity)
 
    @classmethod
    def update(cls):
        cls._update_entities()
        cls._remove_dead_entities()
 
    @classmethod
    def _update_entities(cls):
        for entity in cls.updateable_entites:
            if entity.alive:
                for component in entity.component_update_order:
                    component.update()
 
    @classmethod
    def _remove_dead_entities(cls):
        dead_entities = []
 
        for entity in cls.entities:
                dead_entities.append(entity)
 
                if entity.component_update_order != None:
                    cls.updateable_entites.remove(entity)
 
                cls.entities.remove(entity)     # R.I.P
 
        EventManager.post_event(ET_ENTITY, E_ENTITIES_DESTROYED, dead_entities)
```

The dead entities are removed at the end of every update call. For performance you could remove dead entities a little less frequently.

Also this code is setup to follow the Model-View-Controller architecture, so I have another manager called Entity Representation Manager. Each time a new entity is added it is sent to the Entity Representation Manager via the Event Manager. Then a factory called Representation Factory is called to build a sprite for the entity. The factory will lookup the entity’s name info to determine which subclass of Entity Representation should be called.

This entity representation is only rendered while the entity is alive and when the dead entities are removed from the entity manager, the same will happen in the Entity Representation Manager via the Event Manager again.

As you can see only the model uses components, whereas the view uses a typical class hierarchy because for my game there are only going to be about 5 different Representation Entities used. Depending on the situation, you could also use a component based approach for the view. You could also add a representation component to the entity itself if you don’t mind if the model and the view and a little more connected.

Also for performance you may want to replace the entity name with a enumeration constant. You may also want to add a unique id field to the entity depending on your situation.

The dictionary keys for entity components could also be replaced with enumeration constants.

Thanks for reading!
