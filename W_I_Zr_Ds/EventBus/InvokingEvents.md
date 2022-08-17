---
title: Invoking Events
parent: Event Bus
grand_parent: W_I_Zr_Ds
has_children: false
nav_order: 3
permalink: /W_I_Zr_Ds/EventBus/InvokingEvents
---

# Invoking Events
<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
- TOC
{:toc}
</details>

Events can be invoked in the following ways,

## Direct Invocation
You can invoke an event from a class like so,

```c#
public class MyClass : MonoBehaviour
{
  public EventObject myEvent;
  public GameObject callingObject;

    void Start()
    {
      myEvent.Invoke(callingObject)
    }
}
```
It is important to ensure an event listener has the same calling object set as the first element of its cached objects list. If none does, the event will not be picked up by anything.

For more information, see the sub-section above this.

When invoking like this, it will be picked up by an event listener provided one exists with it's "Parent" set to the calling object. However, when doing this, you need to do control flow yourself to ensure that event should be invoked. For instance, you don't want to invoke a Shoot event when your character is reloading a gun.

## FSM Invocation
If you need complex control flow, it is better to configure a state machine and then send the event to that instead of having the invoking class do it. Provided you have one configured, you can send an event to it like so,

```c#
public class MyClass : MonoBehaviour
{
  public EventObject myEvent;
  public GameObject callingObject;
  public CachedObjectWrapper cachedObjects;
  public FiniteStateMachine fsm;

    void Start()
    {
      fsm.UpdateState(myEvent, callingObject, cachedObjects);
    }
}
```

Depending on how the event is configured, it will now only be invoked if the fsm is in the correct state to receive said event.

For more infromation on FSMs, see the State Machine section.

For more information about cached object wrappers, see the Non Individual State sub-section in the Variables section.
