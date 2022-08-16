---
title: Creating Functions That Don't Return a Value
parent: Variables
grand_parent: W_I_Zr_Ds
has_children: false
nav_order: 6
permalink: /W_I_Zr_Ds/Variables/CreateFunctions
---
# Creating Functions That Don't Return A Value
<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
- TOC
{:toc}
</details>

Variable functions are fairly powerful, but by themselves it's impossible to make anything due to how they must output a value. However, actions fill that gap.

## Actions
Actions are scriptable object functions that do not return values. They are intended to be called via event listeners. All actions must inherit from the ActionBase class, and creating a new action is done like so,

```c#
//It is recommended to put actions under the Events menu, 
//this is done so you don't confuse them for variable functions
[CreateAssetMenu(fileName = "", menuName = "Events/Actions/MyAction")]
public class MyAction : ActionBase
{
    //All actions must override this function, in doing so they have access to cached objects
    public override void Execute(CachedObjectWrapper cachedObjects)
    {        
        Debug.Log("Hello World")
    }
}
```

Actions are where the vast majority of gameplay logic should go. They provide all the functionality of a regular function, but they can be easily swapped out in the inspector and reused everywhere without needing any special architecture or rigid refrences.

For ways to use actions, see the EventListener sub-section in the Events section.