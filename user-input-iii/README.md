![](../images/line3.png)

### User Input III

<sub>[previous](../user-input-ii/README.md#user-content-user-input-ii) • [home](../README.md#user-content-ue4-blueprints)</sub>

![](../images/line3.png)

User input continued...

<br>

---


##### `Step 1.`\|`ITB`|:small_blue_diamond:

Lets add counter clockwise movement. Now we need to add two nodes a **Get Rotating Counter Clockwise** and **Branch** . This checks to see if the counter clockwise <kbd>K</kbd> button is pressed. Connect the execution pin from **Sequence | Then1** to the **Branch** node.  Connect the **RotatingCounterClockwise** pin to the **Branch | Condition** pin. 

![add get rotating counter clockwise and a branch node](images/CheckCounterClockWiseMovementRm16.png)

![](../images/line2.png)

##### `Step 2.`\|`FHIU`|:small_blue_diamond: :small_blue_diamond: 



![connect execution pins](images/ConnectExecPins.jpg)

![](../images/line2.png)

##### `Step 3.`\|`ITB`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond:



![change speed of rotation to 45](images/SpeedOfRotation45.jpg)

![](../images/line2.png)

##### `Step 4.`\|`ITB`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:



![](../images/line2.png)

##### `Step 5.`\|`ITB`| :small_orange_diamond:



![](../images/line2.png)

##### `Step 6.`\|`ITB`| :small_orange_diamond: :small_blue_diamond:




![](../images/line2.png)

##### `Step 7.`\|`ITB`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:



![](../images/line2.png)

##### `Step 8.`\|`ITB`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:



![change auto receive input to player 0](images/AutoReceivePlayer0.jpg)

![](../images/line2.png)

##### `Step 9.`\|`ITB`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:



![](../images/line2.png)

##### `Step 10.`\|`ITB`| :large_blue_diamond:



![](../images/line2.png)

##### `Step 11.`\|`ITB`| :large_blue_diamond: :small_blue_diamond: 

Now the only difference for counter clockwise movement is that the rotation is negative. So *highjack* the output of the **Multiplication** output and add a **Float * Float** node beneath.

![add float multiplication node](images/HighJackMultRm16.jpg)

![](../images/line2.png)


##### `Step 12.`\|`ITB`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: 

Multiply this number by `-1.0`

![multiply by -1](images/MultiplyBy-1Rm16.jpg)

![](../images/line2.png)

##### `Step 13.`\|`ITB`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

*Copy and paste* the Get **Current Angle Deg**, **Addition** and **Set Current Angle Deg** nodes and paste below. *Connect* the output of the **Multiplication** by -1 node to the input of the **+** node. *Connect* the **Execution** pin of the **Branch | True** node to the execution pin of the **Set Current Angle Deg** node.

![connect pins](images/CopyCurrentAngleRm16.jpg)

![](../images/line2.png)

##### `Step 14.`\|`ITB`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

Copy and paste the **Set Relative Rotation** node and *connect* the output of the second **Set** node to the **New Rotation Z (Yaw)** pin of this node.

![copy set relative rotation node](images/CopySetRelativeLocationRm16.jpg)

![](../images/line2.png)

##### `Step 15.`\|`ITB`| :large_blue_diamond: :small_orange_diamond: 

Since we are targetting just the **Static Mesh** by connecting to the **Set Relative Rotation | Target**. *Connect* the **Set Current Angle Deg** execution pin to **Set Relative Rotation**. *Press* the <kbd>Compile</kbd> button.

![connect cube to target](images/CubeToTargetRm16.jpg)

![](../images/line2.png)

##### `Step 16.`\|`ITB`| :large_blue_diamond: :small_orange_diamond:   :small_blue_diamond: 

*Run* the game and test it. Now it works OK as the <kbd>L</kbd> and <kbd>K</kbd> button both work. But there is a design flaw. What I press the L button while pressing the K button without releasing it. Now two booleans are true and they cancel each other out. I want to cancel the other rotation as soon as a new one is detected.

![play game but keys need to be pressed twice](images/RotateCubeBothWays.gif)

![](../images/line2.png)

##### `Step 17.`\|`ITB`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

So in the Button Events add a **Set Rotating Counter Clockwise** to `false` after the <kbd>L</kbd> button is pressed and a **Set Rotating Clockwise** to `false` when the <kbd>K</kbd> button is pressed. *Press* the <kbd>Compile</kbd> button.

![set rotating counter clockwise to false](images/TurnOffOtherDirectionRm16.jpg)

![](../images/line2.png)

##### `Step 18.`\|`ITB`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Now *run* the game and walk into the collision volume. This should finish up this room.

![play game cube rotates correctly](images/RotateCubeClockwise.gif)

![](../images/line2.png)

##### `Step 19.`\|`ITB`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

That's it for **Room 12** and this entire level and walk through. *Press* **Save All** and update **Github** by committing and pushing all the changes made.

![save, commit and push to github](images/GithubRm16.jpg)


| `intro.blueprints`\|`THE END`| 
| :--- |
| **That's All Folks!** Thanks for sticking around. That's it for this lesson. |

![](../images/line.png)

<!-- <img src="https://via.placeholder.com/1000x100/45D7CA/000000/?text=The End!"> -->
![next up next tile](images/banner.png)

![](../images/line.png)

| [previous](../user-input-ii/README.md#user-content-user-input-ii)| [home](../README.md#user-content-ue4-blueprints) |
|---|---|
