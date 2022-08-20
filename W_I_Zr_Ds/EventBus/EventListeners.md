---
title: Event Listeners
parent: Event Bus
grand_parent: W_I_Zr_Ds
has_children: false
nav_order: 2
permalink: /W_I_Zr_Ds/EventBus/EventListeners
---

# Event Listeners
<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
- TOC
{:toc}
</details>

## Delegate Event Listeners
```DelegateEventListener```s are the standard event listeners packaged with W_I_Zr_Ds. They listen for when an event has been invoked and respond by executing all of the ```Actions``` that is associated with said event.

You can create your own event listeners by inheriting from the ```EventListenerBase``` class, for more information visit the appropriate sub-section in the ```API Refrence``` section.
{: .text-grey-dk-000}
{: .fs-3 }

To use an event listener, attach the ```DelegateEventListener``` class to a game object and configure these two sections,

### Event Actions
The event actions section holds a list of event action pairs, which define what ```Actions``` are executed when an event(s) is called. In each event action pair, there is an events and actions column. When an event in the events column is invoked, all ```Actions``` in the actions column are executed.

For more information about ```Actions```, see the ```Creating Functions That Don't Return A Value``` sub-section in the ```Variables``` section.
{: .text-grey-dk-000}
{: .fs-3 }

### Cached Objects
Cached objects are just a ```CachedObjectWrapper```. However, the first entry's key has to be "Parent" and it's game object should the ```CallingObject``` of an event.

For more information about cached object wrappers, see the ```Non Individual State``` sub-section in the ```Variables``` section. Alternatively, for more information about ```CallingObject```s, see the ```Invoking Events``` sub-section.
{: .text-grey-dk-000}
{: .fs-3 }