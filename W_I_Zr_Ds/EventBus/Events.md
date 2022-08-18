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

Event objects are the scriptable objects that have an array of listeners. Whenever an event is invoked, it goes through the listener array and calls a function on each, letting them know it's been invoked. Event objects come bundled with W_I_Zr_Ds so no further configuration is needed to create one.

Note, they're under the Events menu.

After creating an event, you can use it as is, but there are two options that you can change to make the event work better for your specific usecase.

### Global
The is global option makes it so an event listener will respond to the events invocation regardless of what calling object the event was invoked with.

For more information about event invocation and calling objects visit the Invoking Events section

### Queueable
The is queuable option makes it so the event will queue on an FSM if the FSM is in a state where it won't propogate the event. If the FSM is then switched to a state where it can propogate the event, the event will be consumed as usual.

For more information about FSMs, refer to the State Machines section

### Dequeue Layer
This option is only visible if you have Queueable turned on, it determines what state layer on the FSM the event will queue on. You can assign multiple layers to this if you want.

For more information about state layers, refer to the State Machines section