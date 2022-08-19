---
title: Event Bus
parent: W_I_Zr_Ds
has_children: true
nav_order: 4
permalink: /W_I_Zr_Ds/EventBus
---
# Event Bus

## Description

The event system in W_I_Zr_Ds provides you a new way to communicate/send messages between classes.

Traditionally, if a class wanted to send a message to another, it would need a hard refrence to the other class. But, with the event system in W_I_Zr_Ds, classes can communicate via an event scriptable object, which acts as an intermediary. Instead of a hard refrence to a class, the communicator needs a hard refrence to the event. 

However, having a refrence to an event is better than having a refrence to a class due to:

- Testing in isolation: Classes that depend on events can be moved to a different scene for testing without any additional work.
- Easy to change: If a class depends on an event, any event can satisfy it, allowing you to swap them from the inspector.
- Cross scene compatability: An event invoked in one scene can be registered in another scene.