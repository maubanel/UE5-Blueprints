<img src="https://via.placeholder.com/1000x4/45D7CA/45D7CA" alt="drawing" height="4px"/>

### User Input

<sub>[previous](../orbiting-actors-iv/README.md#user-content-orbiting-actors-iv) • [home](../README.md#user-content-ue4-blueprints) • [next](../)</sub>

<img src="https://via.placeholder.com/1000x4/45D7CA/45D7CA" alt="drawing" height="4px"/>

Lets add user input to a basic **Actor** class. We will be using the **L** and **K** button to rotate a cube.

<br>

---


##### `Step 1.`\|`ITB`|:small_blue_diamond:

*Add* a new **Blueprints | Room12** folder. *Create* a new **Blueprint Class** of base **Actor**. Call it `BP_RotateCube.`

![add room12 folder and actor blueprint BP_RotateCube](images/BPRotateCubeActorRm16.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 2.`\|`FHIU`|:small_blue_diamond: :small_blue_diamond: 

Add a **Static Mesh** component to the blueprint. Call it `Cube`. Assign the **Static Mesh** `Cube` (you need to turn on **Engine Assets**) and **Material** `M_Metal_Burnished_Steel`.

![add static mesh component with cube and steel material](images/AssignMeshCubeMaterialRm16.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 3.`\|`ITB`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

*Add* a **Box Collision** *Component* and make the **Box Extent** `200.0`, `600.0`, `100.0`. *Move* the collider in behind the box (opposite of **Red X** axis ).

![scale box collider](images/BoxxCollisionRm16.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 4.`\|`ITB`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Add **BP_Rotate_Cube** to the **Room 12** and center it. Make sure the collision box is in front of cube.

![add BP_Rotate_Cube behond collision box in room 12](images/AddBPToRm16.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 5.`\|`ITB`| :small_orange_diamond:

For housekeeping move this game object into the **Room 12** folder:

![move blueprint to Room 12 folder in world outliner](images/MoveObjectToFolderRm16.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 6.`\|`ITB`| :small_orange_diamond: :small_blue_diamond:

*Add* a **Text Renderer** component to the blueprint.

![add text render component](images/AddTextRenderComponentRm16.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 7.`\|`ITB`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

Change the **Text** to `Press L Key to Rotate Clockwise`. I had to rotate the component by `180` degrees on the **Z** axis to face forward. *Change* **Horizontal Alignment** to `Center` and adjust the **Text Render Color** to contrast with the background. *Select* a larger font size as well! Move text above cube.

![name text, center and change color](images/PressLKeyToRClockRm16.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 8.`\|`ITB`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Right click on **Press L Rotate** Component and press *Duplicate*. Call the new component `Press K Rotate`.

![duplicate text render and call Press K Rotate](images/PressRToRotateRm16.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 9.`\|`ITB`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Change the **Text** to `Press K Key to Rotate Counter Clockwise`. Adjust the location to be below the *L key* text component:

![name second text counter-clockwise](images/PressKRepositionRm16.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 10.`\|`ITB`| :large_blue_diamond:

Go to the game and hit **run**. Look and see if you are happy with the position. Make any size adjustments you need to. 

![test text in game](images/TestInGameRm16.jpg)



<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 11.`\|`ITB`| :large_blue_diamond: :small_blue_diamond: 

Go to the **Event Graph** and *pull off* of the **Event Actor Begin Overlap** and *drag off* off the execution pin. *Select* a **Sequence** node:


![Add sequence node](images/OverlapSequenceRm16.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 12.`\|`ITB`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: 

*Drag* off of the execution pin from the **Sequence Then 0** pin and select **Toggle Visibility (Press L Rotate)**.

![Add toggle visibility node](images/AddToggleVisibilityRm16.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 13.`\|`ITB`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

*Drag* off of the execution pin from the **Sequence Then 1** pin and select **Toggle Visibility (Press K Rotate)**.

![add toggle visibility press k rotate node](images/ToggleVisibillityCounterRm16.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 14.`\|`ITB`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

*Right click* on the empty graph and select the **Event Actor End Overlap** node.

![add end overlap node](images/AddActorEndOverlapRm16-1.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 15.`\|`ITB`| :large_blue_diamond: :small_orange_diamond: 

*Pull off* the execution pin and select another **Sequence** node. *Connect* the outputs of the **Sequence** nodes to the two **Toggle Visibility** nodes:

![add second sequence node](images/AddSecondSequenceRm16.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 16.`\|`ITB`| :large_blue_diamond: :small_orange_diamond:   :small_blue_diamond: 

Add a comment to this group of nodes called `Toggle Text On and Off`.

![add code comments](images/AddComment1Rm16.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 17.`\|`ITB`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

*Run* the game and walk into the collision volume. You will see that the algorithm is backwards. When you are inside the volume the text is off and on when you are outside the volume.

![text backwards in game](images/BackwardsText.gif)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 18.`\|`ITB`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Just ensure that visibility is off when we start open the blueprint and make sure that **Visibility** is `False` on both text rendercomponents:

![set visibility to false on two text components](images/TurnVisibleOff.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 19.`\|`ITB`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Now there is an event trigger for when a button is pressed and released. There is not a trigger for a button being held. So we will create a boolean that sets when a key is held. We need to add two booleans. 

*Add* a new **Boolean** variable called `Rotating Clockwise`, make it **Private** and set the **Category** to `Controls`. *Add* a **Tooltip** that says `Bool to tell us if clockwise button is pressed`.

![add rotating clockwise variable](images/RotatingClockwiseVarRm16.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 20.`\|`ITB`| :large_blue_diamond: :large_blue_diamond:

Go to the **My Blueprints** panel and select the **Rotating Clockwise** with the *right mouse button* and select **Duplicate**:

![duplicate rotating clockwise](images/RIghtClickDupeRm16.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 21.`\|`ITB`| :large_blue_diamond: :large_blue_diamond: :small_blue_diamond:

*Rename* the **Variable** to `RotatingCounterClockwise` and update the **Tooltip**:

![rename to rotatingcounterclockwise](images/RenameCCRm16.jpg)

___


<img src="https://via.placeholder.com/1000x4/dba81a/dba81a" alt="drawing" height="4px" alt = ""/>

<img src="https://via.placeholder.com/1000x100/45D7CA/000000/?text=Next Up - User Input II">

<img src="https://via.placeholder.com/1000x4/dba81a/dba81a" alt="drawing" height="4px" alt = ""/>

| [previous](../orbiting-actors-iv/README.md#user-content-orbiting-actors-iv)| [home](../README.md#user-content-ue4-blueprints) | [next](../user-input-ii/README.md#user-content-user-input-ii)|
|---|---|---|
