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

## Actions
```Actions``` are scriptable object functions that do not return values. They are intended to be called via event listeners. They are where the vast majority of gameplay logic should go. 

They provide all the functionality of a regular function in c#, but they can be swapped out in the inspector and reused everywhere without needing any special architecture or rigid refrences.

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

For ways to use actions, see the ```EventListener``` sub-section in the ```Events``` section.
{: .text-grey-dk-000}
{: .fs-3 }