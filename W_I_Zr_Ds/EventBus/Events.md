---
title: Events
parent: Event Bus
grand_parent: W_I_Zr_Ds
has_children: false
nav_order: 1
permalink: /W_I_Zr_Ds/EventBus/Events
---

# Events
<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
- TOC
{:toc}
</details>

## Event Objects

```EventObject```s are the scriptable objects that have an array of listeners. Whenever an event is invoked, it goes through the listener array and calls a function on each, letting them know it's been invoked. ```EventObject```s come bundled with W_I_Zr_Ds so no further configuration is needed to create one.

To create an ```EventObject``` navigate to Assets > Create > Events > Event Object

After creating an event, you can use it as is, but there are two options that you can change to make the event work better for your specific use case.

### Global
The is global option makes it so an event listener will respond to the events invocation regardless of what ```CallingObject``` the event was invoked with.

For more information about event invocation and ```CallingObject```s visit the ```Invoking Events``` sub-section
{: .text-grey-dk-000}
{: .fs-3 }

### Queueable
The is queuable option makes it so the event will queue on a ```StateLayerObject``` if the state layer's current state will not propogate the event. If the state layer's current state is then switched to a state where it can propogate the event, the event will be consumed as usual.

For more information about ```StateLayerObject```s, refer to the ```State``` sub-section in the ```State Machines``` section
{: .text-grey-dk-000}
{: .fs-3 }

### Dequeue Layer
This option is only visible if you have ```Queueable``` turned on, it determines what ```StateLayerObject``` the event will queue on. You can assign multiple layers to this if you want.

For more information about ```StateLayerObject```s, refer to the ```State``` sub-section in the ```State Machines``` section
{: .text-grey-dk-000}
{: .fs-3 }