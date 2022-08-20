---
title: Non Individual State
parent: Variables
grand_parent: W_I_Zr_Ds
has_children: false
nav_order: 1
permalink: /W_I_Zr_Ds/Variables/NonIndividualState
---
# Non Individual State
<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
- TOC
{:toc}
</details>

Non Individual state is state that does not need to vary between entities. For instance, enemy base health is non individual state as every single enemy instance will have the same base health.

---

## Generic Refrences

For a class to use a variable, the variable must be declared within it via ```GenericRefrence<T>```.
```c#
//replace float with whatever type you want
public GenericReference<float> myVariable;
```

To set the value,
```c#
myVariable.SetValue(1f, new CachedObjectWrapper())
```

In order to get the value,
```c#
myVariable.GetValue(new CachedObjectWrapper())
```

For more information about ```CachedObjectWrapper```s, keep reading. Also note, creating a new  wrapper every time you access the variable is very inefficient, this example is for demonstration purposes only.
{: .text-grey-dk-000}
{: .fs-3 }

You can use the inspector to set the value as well, when doing so you have two options,

### Use override true

When the use override option is set to true, you can manually type in the value you want. This is useful for when you do not want something to be shared, and thus using scriptable objects might be too tedious.

### Use override false

When the use override option is set to false, you can assign a variable scriptable object as the value. This is useful for when you want a piece of state to be shared between scripts.


Provided you have use override set to false, you have to create an instance of a variable scriptable object and drag it into the field on the inspector.

To create a variable scriptable object, navigate to Assets > Create > Variables > Whatever variable you want

---

## Cached Object Wrappers

```CachedObjectWrapper```s are a dictionary with game objects in scene and a key to get each game object with. They also contain a helper function to get objects out from a specific key. They're defined in every event listener and allow scriptable object functions to have in scene refrences. 

Due to how functions and variables are both children of the same parent class, both require a cached object wrapper to access their values.

The recommended way to work with these is to define them in the inspector on event listeners only, when possible. However, if they need to be read from a standard monobehaviour, then create a field in the class like so,

```c#
public CachedObjectWrapper myCache
```

and assign its values in the inspector.