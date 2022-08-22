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
State layer objects are containers that hold a current state value and can be updated with an ```UpdateState``` call. 

```c#
public class MyClass : MonoBehaviour
{
  public EventObject myEvent;
  public GameObject callingObject;
  public CachedObjectWrapper cachedObjects;
  //You can call update state on a StateLayerObject or a FiniteStateMachine, both do the same thing
  public StateLayerObject myLayer;

    void Start()
    {
      myLayer.UpdateState(myEvent, callingObject, cachedObjects)
    }
}
```

All state updates go to the current state. Whenever a state transitions to another, the current state changes.

To create one, navigate to Assets > FSM > State Layer Object

After creation, you need to set the current state value to a state you want to act as the initial state for that layer.

When you pass a ```CachedObjectWrapper``` to update the state, it is used in the state layer object and all child state layer objects to access the current state ```GenericRefrence```.

For more information on ```CachedObjectWrapper```s and ```GenericRefrence```s, visit the ```Non Individual State``` sub-section in the  ```Variables``` section
{: .text-grey-dk-000}
{: .fs-3 }

---

## Finite State Machines
Finite state machines are just a monobehaviour wrapper around a state layer object. What specific state layer object it wraps can be set in the inspector by changing its initial state property. 

They currently do not serve any particular purpose, but in the future they will visually display all states associated with it in a mermaid diagram, so they can be easily previewed.