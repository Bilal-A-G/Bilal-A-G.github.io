---
title: Individual State
parent: Variables
grand_parent: W_I_Zr_Ds
has_children: false
nav_order: 2
permalink: /W_I_Zr_Ds/Variables/IndividualState
---
# Individual State
<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
- TOC
{:toc}
</details>

Individual state is state that needs to vary between entities. For instance, enemy health is individual state as each instance of an enemy needs to have it's own health value.

## IRuntimeVariables
The IRuntimeVariable interface is used to define monobehaviour "anchors" we need to store our state in. 

We need these monobehaviour anchors because you can create multiple instances of the same monobehaviour, each with different data. For instance, you can have 2 enemies each with the same monobehaviour anchor containing their health values, but the health values can change on each individual anchor. 

You can create a monobehaviour anchor like so,

```c#
//The class must inherit from monobehaviour
public class MyRuntimeVariables : MonoBehaviour, IRuntimeVariable
{
    public float myRuntimeVariable;

    public object GetValueFromName(string name)
    {
      //Replace MyRuntimeVariables with the class name
        return typeof(MyRuntimeVariables).GetField(name).GetValue(this);
    }

    public void SetValueFromName(string name, object value)
    {
      //Replace MyRuntimeVariables with the class name
        typeof(MyRuntimeVariables).GetField(name).SetValue(this, value);
    }

    //The only reason this isn't an abstract or something is 
    //because of the type magic needed to get the field from a string
}
```
After creating the monobehaviour anchor, attach it to a game object, and create a new entry for the game object, alongside a key of your choosing in a cached object wrapper (read the ```Non Individual State``` section for more information about those). You can do this like so,

```c#
public class MyClass : MonoBehaviour
{
    //You can and should do this in the inspector instead, 
    //the code here is for demonstration purposes only

    public CachedObjectWrapper myWrapper;
    public GameObject objWithAnchor;

    void Start()
    {
        myWrapper.cache.Add(new CachedObjects(objWithAnchor, "myKey"))
    }
}
```

With the monobehaviour anchor fully setup, you need to create a scriptable object "pointer" that will point to a field on the runtime variables class that was just created. Think of the "pointer" as a middleman between a field on the anchor and a class that wants to access said field.

---

## Generic Runtime Variables
The GenericRuntimeVariable class is a base class that all variable scriptable objects with individual state must inherit from. It is used like so,

```c#
//It is recommended to layout your menus like so for organization purposes
[CreateAssetMenu(fileName = "", menuName = "Modded Variables/Runtime Variables/Float Variable")]
//Replace float with whatever type you want
public class FloatRuntimeVariable : GenericRuntimeVariable<float>{}

//This runtime variable is of type float
```

After doing that, you need to set these fields on the runtime variable to connect it to the anchor,

### Value Key
The value key is the key associated with the game object that the monobehaviour anchor is attached to on the cached object wrapper. If you're following along with the example, this should be "myKey"

### Value Name
The value name is the name of the value on the monobehaviour anchor that you want the runtime variable to "point" to. You must ensure the values type is the same as the runtime variable. If you do not, a type conversion could fail when getting or setting the value. If you're following along with the example, this should be "myRuntimeVariable"

---

For all purposes, generic runtime variables are the exact same as generic variables (non individual state scriptable objects). However, they require a properly setup cached object wrapper to work.


