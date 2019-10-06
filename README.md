

# Build an Apartment
Starter project for the Udacity [VR Developer Nanodegree](http://udacity.com/vr) program.

- Course: VR Scenes & Objects
- Project: Build an Apartment

##Name: Eloumbat Assoua Albert
--
## About
After going through the second phase of the course curriculum, the last part of the stage is implementing the course by building second  project called `Build an Appartment`.  The objectives of this project are:

-   Adding 3D models to a scene
-   Moving, scaling, and rotating 3D models
-   Deploying to your Cardboard Viewer
-   Creating materials and assigning textures
-   Creating animations and triggering them
-   Creating lights and baking them
-   Optimizing a scene for top performance

### Download the Starter Project 

-   Download the source code zip folder for  [Build an Apartment Starter Project](https://github.com/udacity/VR-Scenes-and-Objects_Build-an-Apartment/releases).
    -   The downloaded zip file contains a repository named  `vrnd-build-an-apartment-starter-project`  with the version number appended to the end of the name.
    -   The repository contains a README file with important information about the repository and a Unity project named Build an Apartment.
-   Unzip the repository to a convenient location on your computer.
-   Read the README file.
-   Rename the repository to reflect that it is now your repository, for example,  `vrnd-build-an-apartment-by-firstname-lastname`.
-   Open up the Unity project named Build an Apartment and load the scene named Build an Apartment located in the folder  `Assets > UdacityVR > Scenes`.
    -   You will now see an empty apartment with just a floor, ceiling, some walls, windows, and a door.
    
> **Note** : When you open the unity project, the scene is dark.
___
### Adding 3D models to a scene 
and 
### Creating materials and assigning textures
and
### Creating materials and assigning textures
___
- Before importing any model, it is important to know where to place the model.
To make the room bright enough to place my models, I **added two *temporal directional* lights**. 
	> `DirectionalLightLeft` and `DirectionalLightRight` are *temporal lights sources*, which will be used to just to light up the scene to the placement of 3D model into the apartment. They are nested under the game object `MainLight`
- The first models which I imported are nested under the empty game object called `Food Table` 
	> Table with chairs x3 Free by [3DiZ-ART](https://assetstore.unity.com/packages/3d/props/furniture/table-with-chairs-x3-free-101246)
**Note**: I renamed some imported objects, so I can easily track my work.

- To make a clean an attractive food table I added a round carpet. And nested it under the  `Food Table` object. 
	>  Round Carpet by [OLOF HAGELIN](https://assetstore.unity.com/publishers/6018)
- For internal decorations, I imported a few models from the assets store (Realistic_Furniture_And_Interior_Props_Pack)  for the project.
	-  RFAIPP_Lamp
	- RFAIPP_Sconce_1
	- RFAIPP_Office_Table
	- RFAIPP_Office_Armchair_4
	- RFAIPP_Sofa
	- RFAIPP_Coffee_Table_3
	- Sound_AcousticSystem
	- RFAIPP_Chandelier_3
	- RFAIPP_Bookcase_1
	>  Realistic_Furniture_And_Interior_Props_Packt by [SEVASTIAN MAREVOY](https://assetstore.unity.com/publishers/26980)
- I imported a black clock and added a cs script to make it work with real time.


```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using System;

public class Clock : MonoBehaviour {
    private const float
        hoursToDegrees = 360f / 12f,
        minutesToDegrees = 360f / 60f,
        secondsToDegrees = 360f / 60f;

    public Transform hours, minutes, seconds;
    public bool analog;

    void Update()
    {
        if (analog)
        {
            TimeSpan timespan = DateTime.Now.TimeOfDay;
            hours.localRotation =
                Quaternion.Euler(0f, 0f, (float)timespan.TotalHours * -hoursToDegrees);
            minutes.localRotation =
                Quaternion.Euler(0f, 0f, (float)timespan.TotalMinutes * -minutesToDegrees);
            seconds.localRotation =
                Quaternion.Euler(0f, 0f, (float)timespan.TotalSeconds * -secondsToDegrees);
        }
        else
        {
            DateTime time = DateTime.Now;
            hours.localRotation = Quaternion.Euler(0f, 0f, time.Hour * hoursToDegrees);
            minutes.localRotation = Quaternion.Euler(0f, 0f, time.Minute * minutesToDegrees);
            seconds.localRotation = Quaternion.Euler(0f, 0f, time.Second * secondsToDegrees);
        }
    }
```
> Clock by [WEBCADABRA](https://assetstore.unity.com/publishers/9123)
- The other models where imported fro the `Assets > UdacityVR > Art > Prefabs > Props` which was provided in the downloaded package.
### Moving, scaling, and rotating 3D models
Not all the models which were imported were to scale, right angle or size. Therefore I had to transform some objects.
### Deploying to your Cardboard Viewer
I imported the *GvrEditorEmulator*nfor read rotations, and created two child camera objects, for the left and right eye.
> *ViewPort Rect Set to:* 
Left camera W= 0.5
Right Camera X= 0.5
Position:
Left camera W= 0.31
Right Camera X= -0.31

For each of these cameras, I added a child prefab ( *GvrReticlePointer* ) for the reticle. and executed to check if it ran perfectly.
 
### Creating lights and baking them
In the beginning of the project, the first object I created was a pair of directional lights to light up the scene so that I can place models.
The two types of lights used inside the apartment are spot lights and area lights. 
The spotlights are in real time and the areal lights are baked.

### Creating animations and triggering them
1.	Globe: 
	The next part of this phase was creating an animation. For the globe to rotate on it's y axis, when the cardboard button is pressed and stop when the cardboard button is pressed again.
2. Created a real time clock to show the time, using a C# script (shown above).


## Challenges
1. It took me approximately 50 hours to complete the project. 
2. A small challenge I faces was putting sphere (globe) into the globe holder.

> I added a Suburban Neighborhood - Vorort - Sound Effect - HQ [Youtube](https://www.youtube.com/watch?v=grFF3LPEFz4) music into the background.

## Installs 
	Note: You should already have downloaded and installed Android Studio and the Java SE Development Kit 8 (JDK). Because the game will be deployed on an android device.


### Versions Used
- [Unity LTS Release 2017.4.15](https://unity3d.com/unity/qa/lts-releases?version=2017.4)
- [GVR SDK for Unity v1.170.0](https://github.com/googlevr/gvr-unity-sdk/releases/tag/v1.170.0)


### Directory Structure
- The Unity project is the child directory of the repository and named according to the associated lesson.
- The Unity project is 'cleaned' and includes the `Assets` folder, the `ProjectSettings` folder, and the `UnityPackageManager` folder.


### GVR SDK for Unity
- `GoogleVR` > `Demos` is not included.
- `GoogleVR` > `GVRVideoPlayer.unitypackage` is included.
- Scripts applicable to the course have been updated to reflect Unity's API change from `UnityEngine.VR` to `UnityEngine.XR`.

>**Note:** If for any reason you remove and re-import GVR SDK for Unity v1.170.0, make sure you accept any API update pop-up prompts triggered by Unity. Alternatively, you can manually run the API updater (Unity menu `Assets` > `Run API Updater...`) after the import has completed.


### Related Repositories
- [VR Scenes and Objects - Game Objects](https://github.com/udacity/VR-Scenes-and-Objects_Game-Objects/releases)
- [VR Scenes and Objects - Animations](https://github.com/udacity/VR-Scenes-and-Objects_Animations/releases)
- [VR Scenes and Objects - Cameras](https://github.com/udacity/VR-Scenes-and-Objects_Cameras/releases)
- [VR Scenes and Objects - Lights](https://github.com/udacity/VR-Scenes-and-Objects_Lights/releases)
- VR Scenes and Objects - Build an Apartment

> Written with [StackEdit](https://stackedit.io/).

## About
After going through the second phase of the course curriculum, the last part of this stage is implementing the course by building a project called `Build an Appartment`. This is the second project of the program. The objectives of this project are:

-   Adding 3D models to a scene
-   Moving, scaling, and rotating 3D models
-   Deploying to your Cardboard Viewer
-   Creating materials and assigning textures
-   Creating animations and triggering them
-   Creating lights and baking them
-   Optimizing a scene for top performance

### Download the Starter Project 

-   Download the source code zip folder for  [Build an Apartment Starter Project](https://github.com/udacity/VR-Scenes-and-Objects_Build-an-Apartment/releases).
    -   The downloaded zip file contains a repository named  `vrnd-build-an-apartment-starter-project`  with the version number appended to the end of the name.
    -   The repository contains a README file with important information about the repository and a Unity project named Build an Apartment.
-   Unzip the repository to a convenient location on your computer.
-   Read the README file.
-   Rename the repository to reflect that it is now your repository, for example,  `vrnd-build-an-apartment-by-firstname-lastname`.
-   Open up the Unity project named Build an Apartment and load the scene named Build an Apartment located in the folder  `Assets > UdacityVR > Scenes`.
    -   You will now see an empty apartment with just a floor, ceiling, some walls, windows, and a door.
    
> **Noted** : When you open the unity project, the scene is dark.
___
### Adding 3D models to a scene 
and 
### Creating materials and assigning textures
and
### Creating materials and assigning textures
___
- Before importing any model, it is important to know where to place the model.
To make the room bright enough to place my models, I **added two *temporal directional* lights**. 
	> `DirectionalLightLeft` and `DirectionalLightRight` are *temporal lights sources*, which will be used to just to light up the scene to the placement of 3D model into the apartment. They are nested under the game object `MainLight`
- The first models which I imported are nested under the empty game object called `Food Table` 
	> Table with chairs x3 Free by [3DiZ-ART](https://assetstore.unity.com/packages/3d/props/furniture/table-with-chairs-x3-free-101246)
**Note**: I renamed some imported objects, so I can easily track my work.

- To make a clean an attractive food table I added a round carpet. And nested it under the  `Food Table` object. 
	>  Round Carpet by [OLOF HAGELIN](https://assetstore.unity.com/publishers/6018)
- For internal decorations, I imported a few models from the assets store (Realistic_Furniture_And_Interior_Props_Pack)  for the project.
	-  RFAIPP_Lamp
	- RFAIPP_Sconce_1
	- RFAIPP_Office_Table
	- RFAIPP_Office_Armchair_4
	- RFAIPP_Sofa
	- RFAIPP_Coffee_Table_3
	- Sound_AcousticSystem
	- RFAIPP_Chandelier_3
	- RFAIPP_Bookcase_1
	>  Realistic_Furniture_And_Interior_Props_Packt by [SEVASTIAN MAREVOY](https://assetstore.unity.com/publishers/26980)
- I imported a black clock and added a cs script to make it work with real time.


```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using System;

public class Clock : MonoBehaviour {
    private const float
        hoursToDegrees = 360f / 12f,
        minutesToDegrees = 360f / 60f,
        secondsToDegrees = 360f / 60f;

    public Transform hours, minutes, seconds;
    public bool analog;

    void Update()
    {
        if (analog)
        {
            TimeSpan timespan = DateTime.Now.TimeOfDay;
            hours.localRotation =
                Quaternion.Euler(0f, 0f, (float)timespan.TotalHours * -hoursToDegrees);
            minutes.localRotation =
                Quaternion.Euler(0f, 0f, (float)timespan.TotalMinutes * -minutesToDegrees);
            seconds.localRotation =
                Quaternion.Euler(0f, 0f, (float)timespan.TotalSeconds * -secondsToDegrees);
        }
        else
        {
            DateTime time = DateTime.Now;
            hours.localRotation = Quaternion.Euler(0f, 0f, time.Hour * hoursToDegrees);
            minutes.localRotation = Quaternion.Euler(0f, 0f, time.Minute * minutesToDegrees);
            seconds.localRotation = Quaternion.Euler(0f, 0f, time.Second * secondsToDegrees);
        }
    }
```
> Clock by [WEBCADABRA](https://assetstore.unity.com/publishers/9123)
- The other models where imported fro the `Assets > UdacityVR > Art > Prefabs > Props` which was provided in the downloaded package.
### Moving, scaling, and rotating 3D models
Not all the models which were imported were to scale, right angle or size. Therefore I had to transform some objects.
### Deploying to your Cardboard Viewer
I imported the *GvrEditorEmulator*nfor read rotations, and created two child camera objects, for the left and right eye.
> *ViewPort Rect Set to:* 
Left camera W= 0.5
Right Camera X= 0.5
Position:
Left camera W= 0.31
Right Camera X= -0.31

For each of these cameras, I added a child prefab ( *GvrReticlePointer* ) for the reticle. and executed to check if it ran perfectly.
 
### Creating lights and baking them
In the beginning of the project, the first object I created was a pair of directional lights to light up the scene so that I can place models.
The two types of lights used inside the apartment are spot lights and area lights. 
The spotlights are in real time and the areal lights are baked.

### Creating animations and triggering them
1.	Globe: 
	The next part of this phase was creating an animation. For the globe to rotate on it's y axis, when the cardboard button is pressed and stop when the cardboard button is pressed again.
2. Created a real time clock to show the time, using a C# script (shown above).

## Installs 
	Note: You should already have downloaded and installed Android Studio and the Java SE Development Kit 8 (JDK). Because the game will be deployed on an android device.

## Challenges
1. It took me approximately 50 hours to complete the project. 
2. A small challenge I faces was putting sphere (globe) into the globe holder.

> I added a Suburban Neighborhood - Vorort - Sound Effect - HQ [Youtube](https://www.youtube.com/watch?v=grFF3LPEFz4) music into the background.