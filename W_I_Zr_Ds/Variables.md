---
title: Variables
parent: W_I_Zr_Ds
has_children: true
nav_order: 5
permalink: /W_I_Zr_Ds/Variables
---
# Variables

## Description

The variable system in W_I_Zr_Ds provides you a new way to manage state.

Traditionally, all state had to be shared via global classes, or via direct refrences to other non global classes. But, in W_I_Zr_Ds all non individual state is stored in scriptable objects and all individual state is stored in monobehaviour "anchors" and passed around via event listeners.

This allows you to give anything access to any variable without having to architect your code in really complex ways.
Moreover, you do this without any of the pitfalls of using a singleton/static class as the variables don't introduce unecessary coupling.

For the purposes of organization, functions will be classified as a form of state


