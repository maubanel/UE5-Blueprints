![](../images/line3.png)

### Orbiting Actors IV

<sub>[previous](../orbiting-actors-iii/README.md#user-content-orbiting-actors-iii) • [home](../README.md#user-content-ue4-blueprints) • [next](../user-input/README.md#user-content-user-input)</sub>

![](../images/line3.png)

Orbiting actors continued...

<br>

---


##### `Step 1.`\|`ITB`|:small_blue_diamond:

Now what if we want to have mulitiple sphere blueprints orbiting around the same object. If we had more than one, they would all move one atop each other. What we want to do is add a starting angle (or offset angle) so they are at different distances. *Add* a variable called `Starting Angle` of type **Float** with **Instance Editable** and **Private** set to `true`. Change the **Category** to `Rotation` and add a **Tooltip**.

![add starting angle variable of type float](images/AddStartingAngleRm15.png)

![](../images/line2.png)

##### `Step 2.`\|`FHIU`|:small_blue_diamond: :small_blue_diamond: 

*Drag* the **Get Starting Angle** variable to right after the **Current Angle In Degrees ** that goes to the **Rotate Vector Around Axis** node.

![add get starting angle node](images/DragStartingAngleRm15.png)

![](../images/line2.png)

##### `Step 3.`\|`ITB`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Add an **Addition** node to add the **Current Angle In Degrees** and **Starting Angle** variables together. Send the output to the **AngleDeg** input in **RotateVectorAroundAxis** node.

![add addition node](images/StartingAnglePlusAngleRm15.png)

![](../images/line2.png)

##### `Step 4.`\|`ITB`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Add three more blueprints in the scene. Make sure you assign **Rotate Around Me** to the **Target to Rotate Around**. Have one set to **Starting Angle** `0.0`, the next to `90.0`, the next to `180.0` and the final to `270.0`. *Run* it and it should look like all 4 balls orbit 90° away from each other.

https://user-images.githubusercontent.com/5504953/193809502-e7173448-8ef8-400d-95fe-8ddcf77d3472.mp4

![](../images/line2.png)

##### `Step 5.`\|`ITB`| :small_orange_diamond:

Go back to the editor and rotate the cube so that it is off axis.  We want to test that we are actally rotating based on the center cube's local space.  It should oribit along the axis as the cube rotates.

https://user-images.githubusercontent.com/5504953/193819037-2a90c966-dd97-4104-89fd-ffb6ab79b241.mp4

![](../images/line2.png)

##### `Step 6.`\|`ITB`| :small_orange_diamond: :small_blue_diamond:

Now the sphere is changing location but is not facing the center cube. Lets add some functionality so that the sphere looks at the center point during the rotation so that is translates AND rotates during this sequence. *Right click* on the open graph and look for the **Find Look at Rotation** node:

![add look at rotation node](images/AddLookAtRotationNodeRm15.png)

![](../images/line2.png)

##### `Step 7.`\|`ITB`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

Add a **Get Actor Location** node and hook the the output to the the **Find Look At Rotation** node's **Start** pin:

![connect get actor location to find look at rotation node](images/HookUpStartRotationRm15.jpg)

![](../images/line2.png)

##### `Step 8.`\|`ITB`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

So if the starting point of the look is the sphere location. Then the end point is the center. *Drag* a **Get Target To Rotate Around:** node onto the graph.

![add get target to rotate around node](images/GetTargetToRotateAround.jpg)

![](../images/line2.png)

##### `Step 9.`\|`ITB`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:



![](../images/line2.png)

##### `Step 10.`\|`ITB`| :large_blue_diamond:

Drag off of the pin and select the **Get Actor Location** node which returns the location of the actor we are orbiting around.

![add get actor location node](images/GetActorLocadtionRm15.jpg)

![](../images/line2.png)

##### `Step 11.`\|`ITB`| :large_blue_diamond: :small_blue_diamond: 

*Connect* the output of the **Get Actor Location** node to the **Target** input of the **Find Look at Rotation** node. *Grab* the **Return Value** pin and *select* the **Set Actor Rotation** node:

![connect pins in graph](images/LookAtRotationHookRm15.jpg)

![](../images/line2.png)


##### `Step 12.`\|`ITB`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: 

*Connect* the output of the **Find Look at Rotation | Return Value** pin to the input of the **Set Actor Rotation | New Rotation** pin.

![connect find look at rotatoin to set actor rotation pins](images/ConnectPins3Rm15.jpg)

![](../images/line2.png)

##### `Step 13.`\|`ITB`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

Connect the output execution pin of the **Draw Debug Line** node to the input execution pin of the **Set Actor Rotation** node. Also connect the **Branch | False** before the debug line to the execution pin of the **Set Actor Rotation** node as well. *Press* the <kbd>Compile</kbd> button.

![connect execution pins for draw debug line to set actor rotation](images/SetActorLocationToRotationPinsRm15.jpg)

![](../images/line2.png)

##### `Step 14.`\|`ITB`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

*Run* the game and walk into the collision volume. Now the spheres rotate and continue to face the center and now it looks pretty good. Lets end it here.

![run in game and cubes now rotate to face center](images/Rotate4SpheresRotate.gif)

![](../images/line2.png)

##### `Step 15.`\|`ITB`| :large_blue_diamond: :small_orange_diamond: 

That's it for **Room 11**. Press **Save All** and update **Github** by committing and pushing1all the changes made. 

![alt_text](images/GithubRm15.jpg)

![](../images/line.png)

<!-- <img src="https://via.placeholder.com/1000x100/45D7CA/000000/?text=Next Up - User Input"> -->

![next up next tile](images/banner.png)

![](../images/line.png)

| [previous](../orbiting-actors-iii/README.md#user-content-orbiting-actors-iii)| [home](../README.md#user-content-ue4-blueprints) | [next](../user-input/README.md#user-content-user-input)|
|---|---|---|
