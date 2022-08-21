---
title: State
parent: State Machines
grand_parent: W_I_Zr_Ds
has_children: false
nav_order: 1
permalink: /W_I_Zr_Ds/StateMachines/State
---
# State
<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
- TOC
{:toc}
</details>

## State Objects
State objects are scriptable objects and represent individual states a ```StateLayerObject``` can be in. They are just data containers, used by ```StateLayerObject```s to transition states and invoke events.

For more information on Events, see the ```Events``` and ```Invoking Events``` sub-sections in the ```Event Bus``` section.
{: .text-grey-dk-000}
{: .fs-3 }

To create one, navigate to Assets > FSM > State Object

### On State Enter / On State Exit 
The on state enter/exit fields determine what events will be invoked when the state is transitioned to or away from.

### State Events
The state events determine what events this state will respond to. If the ```StateLayerObject``` this state is attached to gets an ```UpdateState``` call with one of the events in this list, that event will be invoked by the  ```StateLayerObject```.

Furthermore, there's an option to translate a state event to another event. So if you had a state that translated the run event to a jump event, the jump event will be invoked when the ```StateLayerObject``` gets an ```UpdateState``` call with the run event.

### State Transitions
State transitions define when the state will transition to another and what it will transition to. It is a list of event-state pairs, where each event corresponds to a state.

### State Child
The state child is the ```StateLayerObject``` below this state. This is used to delegate ```UpdateState``` calls downwards.

---

## State Layer Objects
State layer objects are a layer containing mutually exclusive states. All state updates go to its current state. Whenever a state transitions to another, it's just changing the current state value on the state layer. All that's needed to configure one is to assign it a state object to act as a default state for that layer.

When you pass a cached object wrapper to update the state, it's used in the state layer objects to access the current state generic refrence.

For more information on cached object wrappers and generic refrences, visit the Variables section

---

## Finite State Machines
The finite state machine class is just a monobehaviour wrapper around a state layer object. What specific state layer object it wraps can be set in the inspector by changing its initial state property. These exist so you don't need to worry about accidentally dragging the wrong state layer object into your scripts that call events. 