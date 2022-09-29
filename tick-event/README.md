![](../images/line3.png)

### Tick Event

<sub>[previous](../components/README.md#user-content-components) • [home](../README.md#user-content-ue4-blueprints) • [next](../tick-event-ii/README.md#user-content-tick-event-ii)</sub>

![](../images/line3.png)

Now the most common game event type is the **Tick Event**. This is what we run every frame. Any game logic that needs to be run every frame (like polling controls to move a player) will be done within the tick event and will happen as fast as the framerate runs.

<br>

---


##### `Step 1.`\|`ITB`|:small_blue_diamond:

Go back to **Maps** and load **IntroToBlueprint2**. The level will not have any lighting built. *Press* the <kbd>Build Button</kbd> to build lighting for the level.

![change to IntroToBlueprint2 map](images/ChangeRooms.png)

![](../images/line2.png)

##### `Step 2.`\|`FHIU`|:small_blue_diamond: :small_blue_diamond: 

Scoot over to **Room 7**. Add a new folder in **Blueprints** and call it `Room7`. Press the <kbd>Add/Import</kbd> button and then select **Blueprint Class**. Select class **Actor**. Call it `BP_Timer`.

![add blueprint bp_timer of actor class](images/AddNewBPActorRm7.jpg)

![](../images/line2.png)

##### `Step 3.`\|`ITB`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Open up the blueprint and *add* a **Text Render** component by *pressing* the **Add Component** button.

![add text render component](images/AddTextRenderComponentRm7.jpg)

![](../images/line2.png)

##### `Step 4.`\|`ITB`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

*Rename* the **Component** to `MS Timer`. *Press* the color and select a shade of green.

![rename component ms timer then change color](images/RenameRecolorRm7.jpg)

![](../images/line2.png)

##### `Step 5.`\|`ITB`| :small_orange_diamond:

Change the **World Size** to `120` and rename the **Text** message to the number `0`.

![set world size to 120 and text to 0](images/WorldSize120Text0Rm7.jpg)

![](../images/line2.png)

##### `Step 6.`\|`ITB`| :small_orange_diamond: :small_blue_diamond:

Add another **Text Render** component and call it `MS Message`. Change the color to yellow and alter the **Text** message to `Time in Milliseconds`.

![add second text render component ms message](images/TimeInMillisecondTextRm7.jpg)

![](../images/line2.png)

##### `Step 7.`\|`ITB`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

*Press* the **Compile** button. If no errors go to the **Event Graph** tab.

![press compile button](images/CompileScriptRm7.jpg)

![](../images/line2.png)

##### `Step 8.`\|`ITB`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

In the **MyBlueprints** tab press **+** next to **Variable** and add a **Float** called `Time in Milliseconds`. Add a **tooltip** with the message `Stores total time in level in milliseconds`. Make sure **Private** is set to `true`.

![add float variable time in milliseconds](images/TimeInMillFloatRm7.jpg)

![](../images/line2.png)

##### `Step 9.`\|`ITB`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

What we want to do is every frame add the number of milliseconds that have passed to this variable. So we need to read it, then add the delta time since last frame. Drag the Variable into the graph and select **Get Time In Milliseconds**.

![get time in milliseconds](images/GetTimeInMSRm7.jpg)

![](../images/line2.png)

##### `Step 10.`\|`ITB`| :large_blue_diamond:

Now *add* a **Float + Float** node which adds two floats together. *Take* the output **Pin** from the **Event Tick** called **Delta Seconds** and *put* it in into the input of the **Addition** node. *Take* the output of the variable **Time in Milliseconds** and put it into the input of the **Addition** node.

![add float + float node](images/AdTimeUpRm7.jpg)

![](../images/line2.png)

##### `Step 11.`\|`ITB`| :large_blue_diamond: :small_blue_diamond: 

Drag the **Time In Milliseconds** variable into the graph and this time select **Set Time In Milliseconds** as we will write this addition to the variable:

![set time in milliseconds](images/SetTimeInMSRm7.jpg)

![](../images/line2.png)


##### `Step 12.`\|`ITB`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: 

*Connect* the Execution pins between the **Event Tick** node and the **Set** node. Also, *connect* the output of the **Addition** node to the input of the **Set Node**.

![connect execution pin and addition to set node](images/SetExecutionAndMilliseconds.jpg)

![](../images/line2.png)

##### `Step 13.`\|`ITB`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

Now, what we want to do is take the output of this variable and have it print to screen. The **MS Timer** text component set to `0` is what we want to target. *Drag* the **MS Timer** component into the scene graph so we have a reference.

![ms timer component on graph](images/MSTimerRefRm7.jpg)

![](../images/line2.png)

##### `Step 14.`\|`ITB`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

*Drag* from the output pin and start typing **Set Text**. This is the node you want to add:

![add set text node](images/SetTextMsRm7.jpg)

![](../images/line2.png)

##### `Step 15.`\|`ITB`| :large_blue_diamond: :small_orange_diamond: 

*Connect* the output **Time in Milliseconds** pin from **Set** node to the **Value** pin in **Set Text**. This automatically adds a **Float to Text** node. *Connect* the execution pins from the same nodes. Add comments to explain the graph (highlight nodes and press the <kbd>C</kbd> key). I split it into the two components that make sense to me. Press the <kbd>Compile</kbd> button:

![connect pins and compile](images/AddCommentsPressCompileRm7Ms.jpg)

![](../images/line2.png)

##### `Step 16.`\|`ITB`| :large_blue_diamond: :small_orange_diamond:   :small_blue_diamond: 

Now go to the game and *drag* the **BP_Timer** blueprint into **Room 7**. If the text is backwards, *rotate* it to face the center of the room.

![drag bp timer to room 7](images/BPTimerInRoom7.jpg)

![](../images/line2.png)

##### `Step 17.`\|`ITB`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

Now run the game and the millisecond counter should count very quickly (hard to see the fractional numbers as they change so fast).

![clock runs in game](images/MillisecondTimer.gif)

![](../images/line2.png)

##### `Step 18.`\|`ITB`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Duplicate MS Timer Message

Lets add the ability to count in whole seconds. Go back to the **BP_Timer** blueprint and *select* the **MS Timer** and **MS Message** components. *Right click* and *select* **Duplicate**.

![duplicate ms timer and ms message](images/DuplicateMSTimerMessageRm7.jpg)

![](../images/line2.png)

##### `Step 19.`\|`ITB`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Now move the new copies to the right so they are next to each other. Change the names of the components to `Sec Timer` and `Sec Message`.

![reneame to sec timer and sec message](images/MoveAndRenameRm7.jpg)

![](../images/line2.png)

##### `Step 20.`\|`ITB`| :large_blue_diamond: :large_blue_diamond:
Change the message in the **Sec Message** component to `Time in Seconds`.

![change message](images/SecMessageTimeInSecsRm7.jpg)

![](../images/line2.png)

##### `Step 21.`\|`ITB`| :large_blue_diamond: :large_blue_diamond: :small_blue_diamond:

Now go back to the **Event Graph** and add a new **Variable** by pressing the **+** button. This time we will make it an integer. A **float** stores a fractional number, an **integer** stores a whole number. Since we are *counting* seconds whole numbers will do. Set the variable to **Variable Type | Integer**. Call it `Time in Seconds`, add a **Tooltip** and make sure that **Private** is set to `true`.

![add an integer variable](images/TimeInSecondsIntRm7.jpg)

![](../images/line.png)

<!-- <img src="https://via.placeholder.com/1000x100/45D7CA/000000/?text=Next Up - Tick Event II"> -->

![next up next tile](images/banner.png)

![](../images/line.png)

| [previous](../components/README.md#user-content-components)| [home](../README.md#user-content-ue4-blueprints) | [next](../tick-event-ii/README.md#user-content-tick-event-ii)|
|---|---|---|
