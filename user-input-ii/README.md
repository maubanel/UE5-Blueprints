![](../images/line3.png)

### User Input II

<sub>[previous](../user-input/README.md#user-content-user-input) • [home](../README.md#user-content-ue4-blueprints) • [next](../user-input-iii/README.md#user-content-user-input-iii)</sub>

![](../images/line3.png)

User input continued...

<br>

---


##### `Step 1.`\|`ITB`|:small_blue_diamond:

*Right click* on the open graph and look for **Event | Keyboard Event | K:**

![add K keyboard event](images/EventKeyboardKRm16.png)

![](../images/line2.png)

##### `Step 2.`\|`FHIU`|:small_blue_diamond: :small_blue_diamond: 

Add two **Set Rotating CounterClockwise**. For the **Pressed** execution pin, set to true and the **Released** pin to false.

![add two set rotating counterclockwise nodes](images/SetCounterclockwiseControlsBoolRm16.png)

![](../images/line2.png)

##### `Step 3.`\|`ITB`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Add the comment `Button Pressed Booleans` to the neds around the **L** and *K* events:

![add code comments](images/Comment2Rm16.png)

![](../images/line2.png)

##### `Step 4.`\|`ITB`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

*Drag* the **Get Rotating Clockwise** node and *drop it* on the graph at the bottom. *Drag off* of the output pin and select a **Branch** node.

![add get rotating clockwise node](images/GetRotatingClockwiseBoolRm16.png)

![](../images/line2.png)

##### `Step 5.`\|`ITB`| :small_orange_diamond:

*Add* a **Sequence** node and attach it to the the **Branch | True** output execution pin. Connect the **Event Tick** execution pin to the input of the **Branch** node.

![add sequence node](images/AttachExecutionPinsSequenceRm16.png)


![](../images/line2.png)

##### `Step 6.`\|`ITB`| :small_orange_diamond: :small_blue_diamond:

We need a variable to adjust the speed of the rotation. *Add* a new variable called `Speed of Rotation` of Type **Float** and make it **Instance Editable** and **Private**. Set the Category to `Controls`. Set the Tooltip to `Set speed in degrees per second`.

*Press* the <kbd>Compile</kbd> button.

Set the **Default Value** to `45.0`.

![add float variable speed of rotation](images/SpeedOfRotationVarRm16.png)

![](../images/line2.png)

##### `Step 7.`\|`ITB`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

We also need a variable to store the current angle of rotation. Add a new variable called `Current Angle` of **Type Float** and make it **Private**. Set the **Category** to `Controls`. Set the **Tooltip** to `speed of rotation in degrees`.

![add float variable current angle deg](images/CurrentAngleDegreesRm16.png)

![](../images/line2.png)

##### `Step 8.`\|`ITB`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

*Drag* a **Speed of Rotation** variable and *add* a **Multiplication** node. Take the output to the **Speed of Rotation** node and attach it to the top multiplication pin.

![add float times float multiplication node](images/FloatByFloatMultiply.png)


![](../images/line2.png)

##### `Step 9.`\|`ITB`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Connect the output **Delta Seconds** from the **Event Tick** to the other end of the **Multiplication** node. This gives us the speed for this one frame.

![connect delta seconds to multiplication node](images/ConnectWithDeltaSecondsRm16.png)

![](../images/line2.png)

##### `Step 10.`\|`ITB`| :large_blue_diamond:



![](../images/line2.png)

##### `Step 11.`\|`ITB`| :large_blue_diamond: :small_blue_diamond: 

Then we need to add this to the existing angle. Place a **Get Current Angle Deg** node:

![add get current angle deg node](images/AddCurrentAngleDegRm16.jpg)

![](../images/line2.png)


##### `Step 12.`\|`ITB`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: 

Then put a **Float + Float** node and add the output of the **Multiplication** node and the **Current Angle Deg** node:

![add multiplication and current angle deg in addition node](images/FloatPFloatRm16.jpg)

![](../images/line2.png)

##### `Step 13.`\|`ITB`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

*Drag* the **Get Speed Of Rotation** node onto the graph.

![get speed of rotation node](images/Rm16GetSpeedOfRotationNodeRm16.jpg)

![](../images/line2.png)

##### `Step 14.`\|`ITB`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

*Right click* and select a **Set Current Angle Deg** node:

![add set current angle deg node](images/SetCurrentAngleVarRm16.jpg)

![](../images/line2.png)

##### `Step 15.`\|`ITB`| :large_blue_diamond: :small_orange_diamond: 

Pull of of the **Float + Float** output pin and add a **Set Current Angle Deg** node. Connect the execution pin of **Branch True** to the input execution pin:

![connect execution pins](images/SetCurrentAngDegRm16.jpg)

![](../images/line2.png)

##### `Step 16.`\|`ITB`| :large_blue_diamond: :small_orange_diamond:   :small_blue_diamond: 

Now we don't want to use **Set Actor Rotation** or the entire actor which includes the text and the collision box will rotate. We just want the **Static Mesh** component mesh to rotate. *Drag* and drop a **Static Mesh** (or whatever you renamed the static mesh) node onto the graph. Pull off of the pin and select **Set Relative Rotation** node.

![alt_text](images/GetCubeComponentRm16.jpg)

![](../images/line2.png)

##### `Step 17.`\|`ITB`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

Now do not have an entire rotation on all axis. We have a float to rotate around the **Z** axis. So *right click* on the **Set Relative Rotation** node's **New Rotation** pin and *select* **Split Struct Pin**:

![split strut pin on set relative rotation node](images/SplitStructPinRm26.jpg)

![](../images/line2.png)

##### `Step 18.`\|`ITB`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:



![](../images/line2.png)

##### `Step 19.`\|`ITB`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:



![](../images/line2.png)

##### `Step 20.`\|`ITB`| :large_blue_diamond: :large_blue_diamond:



![](../images/line2.png)

##### `Step 21.`\|`ITB`| :large_blue_diamond: :large_blue_diamond: :small_blue_diamond:



![](../images/line.png)

<!-- <img src="https://via.placeholder.com/1000x100/45D7CA/000000/?text=Next Up - User Input III"> -->
![next up next tile](images/banner.png)

![](../images/line.png)

| [previous](../user-input/README.md#user-content-user-input)| [home](../README.md#user-content-ue4-blueprints) | [next](../user-input-iii/README.md#user-content-user-input-iii)|
|---|---|---|
