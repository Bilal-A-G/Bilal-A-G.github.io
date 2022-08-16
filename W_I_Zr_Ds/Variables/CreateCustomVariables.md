---
title: Creating Variables of a Custom Type
parent: Variables
grand_parent: W_I_Zr_Ds
has_children: false
nav_order: 5
permalink: /W_I_Zr_Ds/Variables/CreateCustomVariables
---
# Creating Custom Variables
<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
- TOC
{:toc}
</details>

## Generic Variables
The GenericVariable base class contains everything required to make a fully functioning variable scriptable object, however it is a generic and therefore requires the user to create custom, empty, classes to define new variables of a specific type.

This can be done like so,

```c#
//Make the type of the GenericVariable whatever you want, this example is for an audio clip variable
//It is recommended to put custom variables in a seperate menu for organization purposes
[CreateAssetMenu(fileName = "New Audio Clip", menuName = "Modded Variables/AudioClip Variable")]
public class AudioClipVariable : GenericVariable<AudioClip>{}
```
After this, you need to create a field in a class that accepts these variables,

```c#
public class MyClass : MonoBehaviour
{
    //Change the type of the GenericRefrence to whatever you want
    public GenericReference<AudioClip> myClip
}
```
However, there are a few bugs in the inspector with this field. This is because it doesn't have a property drawer defining how the inspector should display it. Luckily, adding one is just as simple as making the variable.

Note, if you want more infromation on editor scripting in W_I_Zr_Ds, visit the Editor Scripting sub-section in the API Refrence section

```c#
//Change the type of the GenericRefrence and GenericRefrenceDrawer to whatever you want
[CustomPropertyDrawer(typeof(GenericReference<AudioClip>))]
public class AudioClipDrawer : GenericReferenceDrawer<AudioClip>{}
```

---

## Variable Functions
Variable functions are functions that return a value. They are interchangable with regular variables, provided the type matches with the generic refrences type. One can be made like so,

```c#
//It is recommended to put variable functions in a seperate variables menu for organization purposes
[CreateAssetMenu(fileName = "", menuName = "Modded Variables/Functions/Multiply Float By Float")]
//Change the type of GenericValue to whatever your function outputs
public class MultiplyFloatByFloat : GenericValue<float>
{
    //This demo class takes a base float, a modifier float and returns the product of the two
    public GenericReference<float> baseValue;
    public GenericReference<float> modifier;

    //Return whatever value your function is supposed to return when something tries to get a value from it
    public override float GetValue(CachedObjectWrapper cachedObjects)
    {
        return baseValue.GetValue(cachedObjects) * modifier.GetValue(cachedObjects);
    }

    //Do whatever your function is supposed to do when something tries to set its value
    public override void SetValue(float value, CachedObjectWrapper cachedObjects)
    {
        return;
    }
}
```
---

Note, variable functions can be chained together to allow for complex behaviour, for instance, here the baseValue field could be another MultiplyFloatByFloat variable function. 

All variable functions should return a value as not doing so will cause a null refrence, if you want a function that doesn't return anything see the appropriate section for it.