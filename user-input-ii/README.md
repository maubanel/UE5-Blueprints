![](../images/line3.png)

### User Input II

<sub>[previous](../user-input/README.md#user-content-user-input) • [home](../README.md#user-content-ue4-blueprints) • [next](../user-input-iii/README.md#user-content-user-input-iii)</sub>

![](../images/line3.png)

User input continued...

<br>

---


##### `Step 1.`\|`ITB`|:small_blue_diamond:

Now we need to update the current angle.  Drag a **Get | CurrentAngleOfRotation** onto the graph.  Add its output with an **Addition** node to the output of the **Multiplication** node.  Send the output of the **Addition** node to a new **Set | CurrentOfRotation** node.

![add K keyboard event](images/getCurrentAngle.png)

![](../images/line2.png)

##### `Step 2.`\|`FHIU`|:small_blue_diamond: :small_blue_diamond: 

Connect the **Triggered** execution pin from the **IA_ClockwiseRotation** node to the **Set CurrentAngleOfRotation** node.  The trigger event will trigger as long as the button is pressed (essentially tick while the user pressed the **L** key).

![add K keyboard event](images/connectExecClock.png)

![](../images/line2.png)

##### `Step 3.`\|`ITB`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

*Drag* a **Cube** component onto the graph.  Pull off of the **Cube** pin and select **Set Relative Rotation** node.  Right click on **New Rotation** and select **Split Struct Pins**. Connect the output of **Set CurrentAngleRotation** into the **Set Relative Rotation | New Rotation Z** pin as well as their respective execution pins.

![add code comments](images/rotateCube.png)

![](../images/line2.png)

##### `Step 4.`\|`ITB`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Press the <kbd>Play</kbd> button and press the <kbd>L</kbd> key.  Nothing happens, why is it not working?

![add code comments](images/lKeyNothing.png)

![](../images/line2.png)

##### `Step 5.`\|`ITB`| :small_orange_diamond:

Select the **BP_RotatingCube** in the level or in the Outliner and change the **Input | Auto Receive Input** from `disabled` to `Player0`.  Actors by default do not take in input events.  This rectifies this problem.

![add code comments](images/receiveInput.png)

![add sequence node](images/.png)


![](../images/line2.png)

##### `Step 6.`\|`ITB`| :small_orange_diamond: :small_blue_diamond:

Now *run* it in game and the cube should rotate clockwise when you press the <kbd>L</kbd> key. The problem is the text rotates with it.  We want the text to stay still.

https://github.com/maubanel/UE5-Blueprints/assets/5504953/da923daa-9703-4c39-ad93-d3e4f54ccad0

![](../images/line2.png)

##### `Step 7.`\|`ITB`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

Now we need to open up **BP_RotateCube** and flatten the hiearchy. Prior the **Box Trigger** and **TextRender** were under the **Cube** so they were inheriting its rotation.  Drag and drop the two child so they are all under the **Default Scene Root**. By having them at the same hiearchy, the static mesh will no longer affect the trigger volume or the text render node.

![add float variable current angle deg](images/undoHiearchy.png)

![](../images/line2.png)

##### `Step 8.`\|`ITB`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

*Press* the <kbd>Play</kbd> button and go up and press the <kbd>L</kbd> key.  Now the cube rotates but the text stays in place.

https://user-images.githubusercontent.com/5504953/194178482-b022c172-e4fd-474a-b6c9-252ac1698e43.mp4

![](../images/line2.png)

##### `Step 9.`\|`ITB`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Go back to the blueprint and select all the nodes used to rotate and press the <kbd>C</kbd> key to add a comment box with the title `Rotate Clockwise`.

![connect delta seconds to multiplication node](images/rotClockComm.png)

![](../images/line2.png)

##### `Step 10.`\|`ITB`| :large_blue_diamond:


![add get current angle deg node](images/counterClock1.png)

![](../images/line2.png)

##### `Step 11.`\|`ITB`| :large_blue_diamond: :small_blue_diamond: 

Then put a **Addition** node and add the output of the **Multiplication** node and the **Current Angle Deg** node.  
![add multiplication and current angle deg in addition node](images/FloatPFloatRm16.png)

![](../images/line2.png)


##### `Step 12.`\|`ITB`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: 

*Right click* and select a **Set Current Angle** node. Send the output of the **Addition** node to the **Set | Current Angle** pin. Connect the execution pin of **Sequence | 0** to **Set Current Angle**.


![get speed of rotation node](images/Rm16GetSpeedOfRotationNodeRm16.png)

![](../images/line2.png)

##### `Step 13.`\|`ITB`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

Now we don't want to use **Set Actor Rotation** or the entire actor which includes the text and the collision box will rotate. We just want the **Static Mesh** component mesh to rotate. *Drag* and drop a **Static Mesh** (or whatever you renamed the static mesh) node onto the graph. Pull off of the pin and select **Set Relative Rotation** node.

![alt_text](images/GetCubeComponentRm16.png)

![](../images/line2.png)

##### `Step 14.`\|`ITB`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

Now do not have an entire rotation on all axis. We have a float to rotate around the **Z** axis. So *right click* on the **Set Relative Rotation** node's **New Rotation** pin and *select* **Split Struct Pin**:

![split strut pin on set relative rotation node](images/SplitStructPinRm26.png)

![](../images/line2.png)

##### `Step 15.`\|`ITB`| :large_blue_diamond: :small_orange_diamond: 

Connect the output of the **Set Current Angle Deg** node to the input of the **Set Relative Rotation** node's **New Rotation Z (Yaw)** pin. Connect the execution pins. Adjust the default Speed of Rotation variable to 45.0 and press the <kbd>Compile</kbd> button. *Press* the <kbd>Compile</kbd> button.

![connecxt set current angle deg to set relative rotation Z pin](images/ConnectCurrentAngleToYawRm26.png)


![](../images/line2.png)

##### `Step 16.`\|`ITB`| :large_blue_diamond: :small_orange_diamond:   :small_blue_diamond: 

*Run* it in game to test if clockwise works. Run into the box and press L (or K for that matter). Hmmm nothing happens.

![cube does not rotate when keys are pressed in game](images/CubeDoesntMove.png)

![](../images/line2.png)

##### `Step 17.`\|`ITB`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

Now go to the game and select the **BP_RotateCube** instance in the level and change the **Auto Receive Input** to `Player 0`.

![get player controller node](images/GetPlayerControllerRm16.png)

![](../images/line2.png)

##### `Step 18.`\|`ITB`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:



![](../images/line2.png)

##### `Step 19.`\|`ITB`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:



![get player controller node](images/flattenHiearchy.png)

![](../images/line2.png)

##### `Step 20.`\|`ITB`| :large_blue_diamond: :large_blue_diamond:



![](../images/line.png)

<!-- <img src="https://via.placeholder.com/1000x100/45D7CA/000000/?text=Next Up - User Input III"> -->
![next up next tile](images/banner.png)

![](../images/line.png)

| [previous](../user-input/README.md#user-content-user-input)| [home](../README.md#user-content-ue4-blueprints) | [next](../user-input-iii/README.md#user-content-user-input-iii)|
|---|---|---|
