# Examples of XML

These are the examples of the XML in use

<a href="lua.md">Lua documentation here</a>

## Scene
- shadowVolume (vec) - World bounds in meters. Everything inside this volume cast shadows. Keep as small as possible. Below is an example of an area with shadows and one without.
    With | Without
    :-:|:-:
    <img src="images/ShadowVolumeWith.png" width="500"> | <img src="images/ShadowvolumeWithout.png" width="500">

## Environment	
  - skybox (string) - The dds file used as skybox. Search path is data/env. Available ones are cloudy, day, moonlit, night, night_clear, and sunset.\
    **Example**: ``` <environment template="sunny" skybox="night.dds"/> ```

  - skyboxtint (vec) - The sky box color tint. Below is an example of it's effect on the world\
    **Example**: ``` <environment template="sunny" skyboxtint="1 0.3 0.3"/> ```\
    <img src="images/Tint.png" width="500">

  - skyboxbrightness (float) - The sky box brightness scale. This can be used to change how dark or light the world is. Below is and example of the difference it can make.\
    **Example**: ``` <environment template="night"  skyboxbrightness="0.04"/>```

   skyboxbrightness="1" | skyboxbrightness="0.05"
   :-:|:-:
   <img src="images/BrightnessTwo.png" width="500"> | <img src="images/BrightnessOne.png" width="500">

  - skyboxrot (float) - The sky box rotation around y axis. Use this to determine angle of sun shadows.\
    **Example**: ``` <environment template="night" skyboxrot="23.3"/>```
    
   skyboxrot="0" | skyboxrot="90"
   :--:|:--:
   <img src="images/SkyboxrotOne.png" width="500"> | <img src="images/SkyboxrotTwo.png" width="500">

  - ambient (float) - Determines how much the skybox will light up the scene.\
    **Example**: ``` <environment template="sunset" ambient="1.4"/>```

  - fogColor (vec) - Color used for distance fog\
   **Example**: ``` <environment template="foggy" fogColor="1 0.4 0.4"/>```\
   <img src="images/Fog.png" width="500">

  - fogParams (vec4) - Four fog parameters: fog start, fog end, fog amount, fog exponent (higher gives steeper falloff along y axis)\
    **Example**: ``` <environment template="foggy" fogParams="0 70 1.5 1.2"/>```

  - sunBrightness (float?) - Light contribution by sun (gives directional shadows)\
  **Example**: ``` <environment template="sunny" sunBrightness="1.2"/>```

  sunBrightness="1.5" | sunBrightness="0.2"
   :--:|:--:
   <img src="images/SunOne.png" width="500"> | <img src="images/SunTwo.png" width="500">

  - sunColorTint (vec) - Color tint of sunlight. Multiplied with brightest spot in skybox.\
    **Example**: ``` <environment template="sunny" sunColorTint="1 0.2 0.2"/>```\
    <img src="images/SunTint.png" width="500">

  - sunDir (int?) - Direction of sunlight. A value of zero will point from brightest spot in skybox.\
    **Example**: ``` <environment template="sunny" sunDir="0"/>```

  - sunSpread (int?) - Divergence of sunlight as a fraction. A value of 0.05 will blur shadows 5 cm per meter\
    **Example**: ``` <environment template="sunny" sunSpread="0.04"/>```

   sunSpread="0" | sunSpread="0.3"
   :--:|:--:
   <img src="images/BlurOne.png" width="300"> | <img src="images/BlurTwo.png" width="300">

  - sunLength (int?) - Maximum length of sunlight shadows. AS low as possible for best performance.\
    **Example**: ``` <environment template="sunny" sunLength="1"/>```
    
   sunLength="4" | sunLength="20"
   :--:|:--:
   <img src="images/LengthOne.png" width="300"> | <img src="images/LengthTwo.png" width="300">

  - sunFogScale (float) - Volumetric fog caused by sunlight\
    **Example**: ``` <environment template="sunny" sunFogScale="0.9"/>```

  - sunGlare (float) - Sun glare scaling\
    **Example**: ``` <environment template="sunny" sunGlare="0.9"/>```
   
   sunGlare="2" | sunGlare="0.5"
   :--:|:--:
   <img src="images/GlareTwo.png" width="500"> | <img src="images/GlareOne.png" width="500">

  - exposure (vec2) - Limits for automatic exposure, min max\
    **Example**: ``` <environment template="sunny" exposure="3.3 1.4"/>```

  - brightness (unknown, possibly a float) - Desired scene brightness that controls automatic exposure. Set higher for brighter scene.\
  **Example**: ``` <environment template="sunny" brightness="1.6"/>```
  
   brightness="1.8" | brightness="0.3"
   :--:|:--:
   <img src="images/ActualBrightnessOne.png" width="500"> | <img src="images/ActualBrightnessTwo.png" width="500">

  - wetness (int?) - Base wetness\
    **Example**: ``` <environment template="sunny" wetness="1"/>```
    
   wetness="0" | wetness="1"
   :--:|:--:
   <img src="images/WetnessOne.png" width="500"> | <img src="images/WetnessTwo.png" width="500">

  - puddleamount (int?) - Puddle coverage. Fraction between zero and one.\
    **Example**: ``` <environment template="sunny" wetness="0.5" puddleamount="0.5"/>```
       
   puddleamount="0.3" | puddleamount="0.6"
   :--:|:--:
   <img src="images/WetgroundTwo.png" width="500"> | <img src="images/WetgroundOne.png" width="500">

  - puddlesize (float) - Puddle size\
    **Example**: ``` <environment template="sunny" wetness="0.5" puddleamount="0.3" puddlesize="0.5"/>```
      
   puddlesize="0.5" | puddlesize="1.5"
   :--:|:--:
   <img src="images/puddlesizeTwo.png" width="500"> | <img src="images/puddlesizeOne.png" width="500">

  - rain (int?) - Amount of rain\
    **Example**: ``` <environment template="night" wetness="1" rain="1"/>```

  - nightlight (bool) - If set to false, all lights tagged night will be removed\
  **Example**: ``` <environment template="night" nightlight="false"/>```

  - ambience (string) - Environment sound path [volume]

## Group 
  - layer (string?, value?) - Override parameter in group. Example dynamic=true will set any parameter named dynamic of every entity in this group to true


# Compound objects

## Instance 
  - file (unknown) - Load prefab instance

## Body 	
  - dynamic (bool) - Set to true for a movable body\
    **Example**: 
    ```xml
    <body pos="1 1 0" dynamic="true"> 
        <vox file="LEVEL/example.vox">
    </body>
     ```

  - desc (string) - Text description. Can be used to make a textbox appear when looking at the object.\
    **Example**: ``` <vox prop="true" pos="1 1 0" file="LEVEL/box.vox" texture="10 0.5" desc="A box"/>```\
    <img src="images/box.png" width="500">

## Vox 			
  - file(string) - Magicavoxel .vox file. Search path data/vox. LEVEL will make it search in the folder with the same name as the xml document.\
    **Example**: ``` <vox pos="0 3 -4" file="LEVEL/example.vox"/>```

  - object (string?) - Vox file sub object. Objects can be named under the outline in magicavoxel.\
   **Example**: ``` <vox pos="4.5 1 -1" file="LEVEL/car.vox" object="wheel"/>```\
  <img src="images/outline.png" width="200">

  - pos (vec3) - Position in meters\
   **Example**: ``` <vox pos="0 3 -4" file="LEVEL/position_example.vox"/>```

  - rot (vec3) - Rotation in degrees (e.g. 0-360) (example value to rotate backwards: rot="0 180 0")

  - scale (int?) - Voxel scaling. Use for background objects only with disabled collisions. Below the object on the left has a scale of 1 and the one on the right has a scale of 0.2.\
    **Example**: ``` <vox pos="2.7 1 0" file="LEVEL/box.vox" scale="0.2"/>```\
  <img src="images/scale.png" width="500">

## Light		
  - type (string) - Type of light source. Can be sphere, cone or area\
    **Example**: ``` <light pos="0 2.5 0" glare="0.2" scale="3" type="area" size="0.3 1.5"/>```
   
   type="sphere" | type="cone" | type="area" 
   :--:|:--:|:--:
   <img src="images/sphereLight.png" width="350"> | <img src="images/coneLight.png" width="350"> | <img src="images/areaLight.png" width="350">

  - color (vec) - Light color RGB value. Do not include intensity here. All values should be in between zero and one.\
    **Example**: ``` <light pos="0 2.5 0" scale="3" type="cone" color="1 0.9 0.3"/>```\
  <img src="images/lightcolor.png" width="500">

  - scale (float?) - Light intensity\
    **Example**: ``` <light pos="0 2.5 0" glare="0.2" scale="3" type="area" size="0.3 1.5"/>```
     
   scale="1" | scale="3"
   :--:|:--:
   <img src="images/lightScaleOne.png" width="500"> | <img src="images/lightScaleTwo.png" width="500">

  - angle (int)	- Cone angle in the case of a cone light type\
    **Example**: ``` <light pos="0 2.5 0" scale="3" type="cone" angle="65"/>```
     
   angle="30" | angle="90"
   :--:|:--:
   <img src="images/lightAngleOne.png" width="500"> | <img src="images/lightAngleTwo.png" width="500">

  - penumbra (int?) - Penumbra angle in the case of a cone type
    **Example**: ``` <light pos="0 2.5 0" scale="3" type="cone" penumbra="65"/>```
     
   penumbra="0" | penumbra="50"
   :--:|:--:
   <img src="images/penumbraOne.png" width="500"> | <img src="images/penumbraTwo.png" width="500">

  - size (float) - Radius of source in case of sphere. Width and height in case of area light. Specified in meters.\
    **Example**: ``` <light pos="-3 2 0" scale="3" type="area" size="0.4 1"/>```
     
   size="0.5" | size="2"
   :--:|:--:
   <img src="images/lightsizeOne.png" width="500"> | <img src="images/lightSizeTwo.png" width="500">

   size="0.5 0.3" | size="2 0.3"
  :--:|:--:
   <img src="images/areaOne.png" width="500"> | <img src="images/areaTwo.png" width="500">

  - unshadowed (float) - A small distance in meters that is always unshadowed. Useful to avoid shadows from a nearby light fixture and/or emissive light surface.\
    **Example**: ``` <light pos="0 2 0" scale="3" type="cone" unshadowed="0.5"/>```
     
   unshadowed="0" | unshadowed="1"
   :--:|:--:
   <img src="images/unshadowedTwo.png" width="500"> | <img src="images/unshadowedOne.png" width="500">

  - fogscale (float?) - Volumetric fog amount\
    **Example**: ``` <light pos="0 2 5" rot="90 0 0" scale="2" type="cone" fogscale="0.3"/>```
   
   fogscale="0" | fogscale="5"
   :--:|:--:
   <img src="images/lightFogscaleOne.png" width="500"> | <img src="images/lightFogscaleTwo.png" width="500">

  - fogiter (float?) - Quality of volumetric fog. Usually leave at one. For very bright and important lights, you may set increase it to avoid flickering.\
    **Example**: ``` <light pos="0 2 6" rot="90 0 0" scale="4" type="cone" fogscale="2" fogiter="1"/>```\
   <img src="images/lightFogiter.png" width="500">

  - sound (string) - path [volume]
  
  - glare (int?) - Glare amount\
    **Example**: ``` <light pos="2 1.3 0" rot="90 0 0" scale="2" type="cone" glare="0.4"/>```
   
   glare="0.3" | glare="1"
   :--:|:--:
   <img src="images/lightGlareOne.png" width="500"> | <img src="images/lightGlareTwo.png" width="500">

## SpawnPoint
  - pos (vec3) - Position in meters. player will spawn at the lowest point with no material above it.\
    **Example**: ``` <spawnpoint pos="10 0 -3"/>```
   
  - rot (vec3) - Rotation in degrees (e.g. 0-360) (example value to rotate backwards: rot="0 180 0")\
    **Example**: ``` <spawnpoint pos="1.5 0 2" rot="0 90 0"/>```
   

## Location

## Enemy

## VoxScript 
    - file (string) - possibly the voxscript file to be executed?

## Joint 
  - type (string) - ball, hinge or prismatic\
    **Example**: ``` <joint pos="-0.5 0 0" type="ball"/>```
   
   type="ball" | type="hinge" | type="prismatic" 
   :--:|:--:|:--:
   <img src="images/ballHinge.gif" width="350"> | <img src="images/hingeJoint.gif" width="350"> | <img src="images/prismaticJoint.gif" width="350">

  - size (float) - The joint attachment point search radius\
    **Example**: ``` <joint pos="-0.5 0 0" type="ball" size="0.2"/> ```
  - rotstrength (float) - Rotational strength of joint. Set to zero for freely rotating joint.\
    **Example**: ``` <joint pos="1.3 0.2 0" type="prismatic" rotstrength="0.1"/>```
   
   rotstrength="0" | rotstrength="0.3"
   :--:|:--:
   <img src="images/stiffJointTwo.gif" width="500"> | <img src="images/stiffJointOne.gif" width="500">

  - rotspring (float) - Springyness of joint. Set to zero for pure damper. Keep below one to stay stable.\
    **Example**: ``` <joint pos="1.3 0.2 0" type="prismatic" rotspring="0.1"/>```
   
   rotspring="0" | rotspring="0.3"
   :--:|:--:
   <img src="images/springJointOne.gif" width="500"> | <img src="images/springJointTwo.gif" width="500">

  - collide (bool) - Allow collisions between jointed shapes\
    **Example**: ``` <joint pos="-5 0 -0.3" type="ball" rotstrength="0.05" collide="true"/>```

  - limits (int?) - Optional min and max angle of hinge rotation\
    **Example**: ``` <joint pos="-0.5 0 0" rot="0 90 0" type="prismatic" limits="-1 1">```\
   <img src="images/limits.gif" width="500">

  - sound (bool) -Joint makes sound.\
    **Example**: ``` <joint pos="-0.5 0 0" type="hinge" rotstrength="0.2" sound="true"/>```

## Water	
  - type (string) - Geometry type: box or polygon\
    **Example**: ``` <water pos="0 1.5 0" size="1 1" type="box"/>```
  - size (Vec2) - Size in meters along X and Z axes. Only applicable to box\
    **Example**: ``` <water pos="0 1.5 0" size="0.9 3" type="box"/>```

  - depth (int?) - Depth along negative y axis\
    **Example**: ``` <water pos="0 2 0" depth="2.4"/>```

  - wave (float) - Large wave amount\
    **Example**: ``` <water pos="0 2 0" wave="1"/>```
   
   wave="0.5" | wave="2"
   :--:|:--:
   <img src="images/waveSizeTwo.png" width="500"> | <img src="images/waveSizeOne.png" width="500">

  - ripple (float) - Small wave amount\
    **Example**: ``` <water pos="0 2 0" ripple="0.9"/>```
   
   ripple="0.2" | ripple="2"
   :--:|:--:
   <img src="images/rippleAmountOne.png" width="500"> | <img src="images/rippleAmountTwo.png" width="500">

  - motion (float) - Sideways motion amount\
    **Example**: ``` <water pos="0 1 0" motion="1.2"/>```
   
   motion="0" | motion="2"
   :--:|:--:
   <img src="images/waterMotionOne.gif" width="500"> | <img src="images/waterMotionTwo.gif" width="500">

  - foam (float) - Foam amount\
    **Example**: ``` <water pos="0 1.5 0" foam="1.4"/>```
   
   foam="0.5" | foam="4"
   :--:|:--:
   <img src="images/foamOne.png" width="500"> | <img src="images/foamTwo.png" width="500">


## VoxBox 		
  - size (vec) - Size in voxels
  - brush (string) - Magicavoxel file to use as brush or 3D texture
  - object (string?) - Brush file subobject, if any
  - offset (vec) - Offset into voxel brush, in voxels along x, y and z
  - material (string) - Set material if no brush is given. Should be one of glass, wood, masonry, plaster, metal, heavymetal, rock, dirt, foliage, unphysical
  - color (vec) - Color tint, RGB values between zero and one
  - pbr (vec4) - Additinal PBR properties - reflectivity, shinyness, metalness and emissive. Emissive is in range 0-32, the others in range 0-1

## Voxagon 
    - brush (string) - Magicavoxel file to use as brush or 3D texture
    - object (string) - Brush subobject, if any
    - offset (vec) - Offset into voxel brush, in voxels along x, y and z
    - axis (str) - Extrusion axis as seen in vox file. For floors this is z, for walls it is y
    - extrude (unknown) - Extrution along axis

## Vehicle	
    - driven (bool) - 
    - sound (string) - Sound preset (small, medium, truck, v8), optional pitch
    - spring (float) - Stiffness of suspension spring
    - damping (float) - Suspension damping
    - topspeed (float) - Top speed in km/h
    - acceleration (float) - Combine with strength to control how fast the car accelerates.
    - strength (float) - Engine strength
    - antispin (float) - Prevent wheels from spinning during acceleration. between zero and one.
    - antiroll (float) - Prevent vehicle from tipping over. Similar to lowering the center of mass, but looks less weird
    - difflock (float) - Differential control. Zero is open differential, one is fully locked. Use zero for regular cars, one for heavy vehicles.
    - steerassist (float) - Arcade steering. This improves handling a lot. Should normally never be more than 1.0
    - friction (float) - Tire friction. For most cars leave as is. For small cars and sports car, increase slightly.

## Wheel 
    - drive (vec2) - Control how much of the engine power is applied to wheel. Normally 0.0 or 1.0.
    - steer (float)
    - travel (vec2) - Suspension travel distance from normal position, min max along Y axis.
    
## Rope 
    - size (float) - Rope attachment point radius
    - color (vec) - Rope color
    - slack (float) - Desired slack. Can be negative for more tension.
    - strength (float) - Rope strength. Negative is infinite.
    - maxstretch (float) - Rope breaks if stretching more than this
    Exemple of rope usage
    
### Usage
```xml
<rope>
    <!-- Attach points -->
    <location pos="1.0 1.0 0.0"/>
    <location pos="10.0 1.0 0.0"/>
</rope>
```
    
    
## Boundary

## Screen
    - pos (vec3) - Position in meters
    - rot (vec3) - Rotation in degrees (e.g. 0-360) (example value to rotate backwards: rot="0 180 0")
    - size (vec2) - width and height
    - bulge (vec2) - bulge height at center
    - resolution (vec2) - render resolution
    - script (string) - script location relative to data folder
    - enabled (bool) - 
    - interactive (false)
    - emissive (float?)
    - fxraster (int or bool?)
    - fxca (int or bool?)
    - fxnosie( int or bool?)
    - fxglitch(int or bool?)



## Trigger
    - type(string)
    - size (int)
    - sound (string)
    - soundramp (float)
    
# Script
    - file (string) -

