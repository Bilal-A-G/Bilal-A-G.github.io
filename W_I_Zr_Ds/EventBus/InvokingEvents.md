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

```EventObjects``` can be invoked in the following ways,

## Direct Invocation
Direct invocation, is when an event is invoked directly from a class. When invoking like this, it will be picked up by an event listener provided one exists with it's "Parent" set to the ```CallingObject```. However, when doing this, you need to do control flow yourself to ensure that event should be invoked. For instance, you don't want to invoke a Shoot event when your character is reloading a gun.

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
It is important to ensure an event listener has the same ```CallingObject``` set as the first element of its ```CachedObject```s list. If none does, the event will not be picked up by anything.

For more information on ```CachedObjects```, see the ```Individual State``` sub-section in the ```Variables``` section. Alternatively, keep reading for more information about ```CallingObject```s
{: .text-grey-dk-000}
{: .fs-3 }

---

## State Machine Invocation
If you need complex control flow, it is better to configure a state machine and send the event there instead of having the invoking class do it. Depending on how the event is configured, it will now only be invoked if a ```StateLayerObject``` is in the correct state to receive said event.

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

For more information on State Machines, see the ```State``` sub-section in the ```State Machines``` section. Alternatively, for more information about ```CachedObjectWrappers```, see the ```Non Individual State``` sub-section in the ```Variables``` section.
{: .text-grey-dk-000}
{: .fs-3 }

---

## Calling Objects
```CallingObjects``` are game objects that an event must be called with and every event listener's "Parent" property must be. Events are only registered on an event listener if the ```CallingObject``` it was called with is the same as the event listener's "Parent". They allow different instances of the same entity in scene to use the same events without any "misfires".

For instance, if a scene has two instances of one enemy prefab (enemy one and enemy two), both with identical event listeners, listening for identical events. If enemy one gets close to the player and invokes the attack event, enemies one and two will register the same event and attack. 

However, with ```CallingObjects```, the "Parent" property on the event listener as well as the ```CallingObject``` each event is fired with can be set to something instance based, ex the prefab's game object. Then, if enemy one invokes the attack event, enemy two won't register the same event because its ```CallingObject``` and event listener "Parent" is set to its game object, not enemy one's game object.

For more information about the "Parent" property on event listeners, see the ```Event Listeners``` sub-section.
{: .text-grey-dk-000}
{: .fs-3 }