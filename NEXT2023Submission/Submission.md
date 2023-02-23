---
title: Submission
parent: Next 2023 Submission
has_children: false
nav_order: 1
permalink: /Next_2023_Submission/Submission
---
# Submission
## Description
Ubisoft NEXT is an annual game development competition open to university students and new graduates all across Ontario, the 
competition has several categories such as Game Design, 3D Art, Animation, Technical Art, etc.

This project is my submission to Ubisoft NEXT 2023, for the Programming category.

For more information about the game, navigate to the [Game](http://example.com/) sub section

For more information about the engine, navigate to the [Ga_U_SS](/Next_2023_Submission/Ga_U_SS) sub section

## Running
### Via an IDE (Visual Studio or Rider preferred)
This project uses Premake 5 as its build system

To build, first download the [Repository](//github.com/Bilal-A-G/NEXT-Submission-2023) for this project on Github, unzip it, and 
double click the "GenerateProjectFiles.bat" file to generate the .sln, which will be for Visual Studio 2019 by default

The contents of the .bat file are:
```
call external\premake\premake5.exe vs2019
PAUSE
```
Feel free to change the ```vs2019``` part of the call to whatever version of Visual Studio you are using

Lastly, open the .sln and build the .exe (Ctrl B) and then run it (Ctrl F5)

### Via the release
Download the release from this projects Github repository, then unzip it and double click the .exe