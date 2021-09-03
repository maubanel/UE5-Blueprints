<img src="https://via.placeholder.com/1000x4/45D7CA/45D7CA" alt="drawing" height="4px"/>

### Rotation

<sub>[previous](../tick-event-ii/README.md#user-content-tick-event-ii) • [home](../README.md#user-content-ue4-blueprints) • [next](../rotation-ii/README.md#user-content-rotation-ii)</sub>

<img src="https://via.placeholder.com/1000x4/45D7CA/45D7CA" alt="drawing" height="4px"/>

We will be rotating an object in 3-D space through blueprints. Now there are two common ways of representing rotations in games.  One is with **[Eulers](https://en.wikipedia.org/wiki/Euler_angles)** and the other is with **[Quaternions](https://en.wikipedia.org/wiki/Quaternions_and_spatial_rotation)**. In the editor the rotations are represented as **Eulers** with the **XYZ** axis rotation in **degrees**.

<br>

---


##### `Step 1.`\|`ITB`|:small_blue_diamond:

*Create* a new folder called `Room8`. *Add* a new **Blueprint Class** of type **Actor** and call it `BP_RotateObject`. *Open up* the **blueprint**:

![create rrom 8 folder add a new blueprint](images/NewBluePrintActorClassRm8.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 2.`\|`FHIU`|:small_blue_diamond: :small_blue_diamond: 

*Add* a **Static Mesh** component to the blueprint. *Change* the **View Options** to see **Engine Content**. *Select* the **Cube** static mesh:

![add static mesh component](images/StaticMeshCubeRm8.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 3.`\|`ITB`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

*Assign* the **M_Metal_Burnished_Steel** Material.

![assign M_Metal_Burnished_Steel](images/AssignMatRm8.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 4.`\|`ITB`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

*Rename* the static mesh to `Rotating Cube`.

![rename to rotating cube](images/RenameComponentRm8.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 5.`\|`ITB`| :small_orange_diamond:

Now go to the **Event Graph** tab. We will be rotating on the **Z**, **X** and **Y** axis. So lets put in a **Sequence** node to keep our graph neet. Since this needs to animate every frame we will use the **Tick Event** and connect its execution pin to the **Sequence** node:

![add sequence node](images/SequenceNodeForRotation.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 6.`\|`ITB`| :small_orange_diamond: :small_blue_diamond:

Now we want a switch in the editor to turn each axis on or off. We will use a **boolean** that is exposed to the editor to accomplish this. *Add* a new **Variable** by pressing the **+** button and call it `bRotateOnZ`. Make sure it is type **Boolean** and make sure that **Instance Editable** is set to `true`. Also since no other object will access this, set the **Private** access to `true`. *Add* a **tooltip** `Rotate on Z Axis, Yaw, Shaking Head No`.

![adjust variable settings](images/RotateOnZRm8.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 7.`\|`ITB`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

Drag the **Rotate On Z** boolean to the graph and select **Get**.

![add rotate on z](images/GetZRm8.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 8.`\|`ITB`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

*Grab* the pin coming of the **Rotate On Z** node and select **Branch**. Again this is the same as an if statement.

![add branch node](images/BranchOffRotateZRm8.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 9.`\|`ITB`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Attach the Execution pins from Sequence 0 to Branch.

![attach execution pin from sequence 0 to branch](images/RefToRotatingCubeRm8.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 10.`\|`ITB`| :large_blue_diamond:

*Drag and drop* the **Rotating Cube** component into the scene graph to create a reference.

![rotating cube reference](images/RefToRotatingCubeRm8-1.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 11.`\|`ITB`| :large_blue_diamond: :small_blue_diamond: 

*Drag off* of the **Rotating Cube** pin and find the **Add Relative Rotation** node and *add* it to the scene graph.

![add relative rotatation](images/AddRelativeRotation.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>


##### `Step 12.`\|`ITB`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: 

*Drag* the execution pin from the **True** output of the Branch and *connect* it to the **Add Relative Rotation**. This will only run the rotation if this boolean is set to **True**.

![connect execution pins](images/SetRotateTruePinsRm8.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 13.`\|`ITB`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

We need another variable to track how many degrees per second the object will rotate in. We need to accept both positive and negative values. Flipping the sign will change the direction of rotation. Create a new **Variable** called `Degrees Per Second` of type **Float** and set **Instance Editable** to `true` and **Private** to `true`. If you would like you could restrict the **Value Range** from `-360` to `360`.

![call variable degrees per second](images/DegreesPerSecond.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 14.`\|`ITB`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

Now we can set the speed of how many degrees per second that we would like to turn but how do we then know what each frame takes. Not all frames will be the same length so we can't just divide the **Degrees Per Second** by the frame rate. The easiest way is to multiply it by the delta time. Lets say this is 1/60th of a second or .01666. If we multiply our value of 45 (degrees per second) times .01666 we will get our time since last frame = .747 degrees.

We need a variable to keep this number in. *Create* a new **Float** variable called` Degrees Since Last Frame` and set **Private** to `true`. Add a **Tooltip** such as `Degrees to turn this frame`.

![create new float variable degrees since last frame](images/DegreesSinceLastFrame.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 15.`\|`ITB`| :large_blue_diamond: :small_orange_diamond: 

Drag and drop the **Degrees Per Second** variable to the graph and select **Get**. *Right click* on the open graph and find a **Float * Float** node.

![add degrees per second and float times float node](images/GetDegreesPerSecRm8.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 16.`\|`ITB`| :large_blue_diamond: :small_orange_diamond:   :small_blue_diamond: 

*Connect* the **Delta Seconds** from the **Event Node** to the **Multiply** node, and the output of **Degrees Per Second** to the **Multiply** node. *Add* a **Set Degree Since Last Frame** node reference to the variable. *Send* the result of this multiplication to the setter input for the **Set** node.

![connect pins and add set degree since last frame](images/ConnectSpeedPinsRm8.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 17.`\|`ITB`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

Now *break* the pins between the **Tick** event and **Sequence**. *Route* this execution through the **Set** node.

![route execution pin through set node](images/ReconnectSetterRm8.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 18.`\|`ITB`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Now go back to the **Add Relative Rotation** node and *right click* on **Delta Rotation**. We just want to affect the *Z* axis so we will *select* **Split Struct Pin**:

![split struc pin](images/SplitRotationStructPinsRm8.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 19.`\|`ITB`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Now *drag* the **Degrees Since Last Frame** variable into the scene graph and select **Get**.

![add get degrees since last frame](images/DegreesLastFrameGetterRm8.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 20.`\|`ITB`| :large_blue_diamond: :large_blue_diamond:

*Connect* the output of **Degrees Since Last Frame** with the input on the **Rotation** node into the **Delta Rotation Z (Yaw)** pin.

![connect output of degrees since last frame](images/ConnectOuputRm8.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 21.`\|`ITB`| :large_blue_diamond: :large_blue_diamond: :small_blue_diamond:

Add a comment to the latest work.

![add code comments](images/CommentSection1Rm8.jpg)

___


<img src="https://via.placeholder.com/1000x4/dba81a/dba81a" alt="drawing" height="4px" alt = ""/>

<img src="https://via.placeholder.com/1000x100/45D7CA/000000/?text=Next Up - ADD NEXT TITBE">

<img src="https://via.placeholder.com/1000x4/dba81a/dba81a" alt="drawing" height="4px" alt = ""/>

| [previous](../tick-event-ii/README.md#user-content-tick-event-ii)| [home](../README.md#user-content-ue4-blueprints) | [next](../rotation-ii/README.md#user-content-rotation-ii)|
|---|---|---|
