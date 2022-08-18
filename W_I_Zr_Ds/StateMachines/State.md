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
State objects are a specific state that a FSM layer can be in. They can be created the same way as any scriptable object, and are located under the FSM section of the create menu.

State objects handle control flow by propogating events and transitioning themselves to other states in response to certain events.

An event is propogated when it's invoked from the FSM, and thus registers on an event listener. However, when an event is not propogated, it either gets added to a queue, or gets propogated down, where the child state gets updated with the event. If after passing through every state later, it's still not responded to, it will be ignored.

After creating one, there are a few options that needs to be set before it can be used,

### On State Enter / On State Exit 
The on state enter/exit fields determine what events will be propogated when the state is transitioned to or away from.

### State Actions
The state actions determine what events will be propogated by this state. Furthermore, there's an option to translate an event to another. So if you had a state that translated the run event to a jump event, the jump event will be propogated when the FSM is updated with the run event.

### State Transitions
State transitions define when the state will transition to another and what it will transition to. It is a list of event-state pairs, where each event corresponds to a state to transition to. For instance, if there was an entry on the transitions list where the event was run and the state was running. If the state got updated with the run event, it will transition to the running state.

### State Child
The state child is the state layer below this state. This is used to delegate events downwards.

---

## State Layer Objects
State layer objects are a layer containing mutually exclusive states. All state updates go to its current state. Whenever a state transitions to another, it's just changing the current state value on the state layer. All that's needed to configure one is to assign it a state object to act as a default state for that layer.

When you pass a cached object wrapper to update the state, it's used in the state layer objects to access the current state generic refrence.

For more information on cached object wrappers and generic refrences, visit the Variables section

---

## Finite State Machines
The finite state machine class is just a monobehaviour wrapper around a state layer object. What specific state layer object it wraps can be set in the inspector by changing its initial state property. These exist so you don't need to worry about accidentally dragging the wrong state layer object into your scripts that call events. 