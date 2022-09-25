![](../images/line3.png)

### Constructor & Begin Play II

<sub>[previous](../constructor-begin/README.md#user-content-constructor--begin-play) • [home](../README.md#user-content-ue4-blueprints) • [next](../collision/README.md#user-content-collision-events)</sub>

![](../images/line3.png)

The Constructor runs in different scenarios.  The **Begin Play** event **ONLY** runs when you press **Run** in the editor.  It always runs **AFTER** the construction script runs.

<br>

---


##### `Step 1.`\|`ITB`|:small_blue_diamond:

Go to the **Blueprints | Room1** folder and right click on **BP_TextOnConstructor** and select **Duplicate**:

![duplicate BP_TextOnConstructor](images/DuplicateBPRm1.png)

![](../images/line2.png)

##### `Step 2.`\|`FHIU`|:small_blue_diamond: :small_blue_diamond: 

Rename the file to `BP_TextInBeginPlay`.

![rename blueprint to BP_TextOnBeginPlay](images/RenameBeginPlayRm1.png)

![](../images/line2.png)

##### `Step 3.`\|`ITB`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Drag the new **BP_TextOnBeginPlay** blueprint into the room, next to the other text blueprint.

![drag BP_TextOnBeginPlay in room](images/DragBPInRoom1.png)

![](../images/line2.png)

##### `Step 4.`\|`ITB`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Drag and drop the blueprint instances from the **Outliner** into the **Room 1** folder.

![put both blueprints in Room folder in world outliner](images/WorldOutlinerCleanupRm1.png)

![](../images/line2.png)

##### `Step 5.`\|`ITB`| :small_orange_diamond:

*Open* **BP_TextInBeginPlay**, enter the **Construction Script** tab and *copy* and *delete* all the nodes to the right of the **Construction Script** node.

![copy and delete construction script nodes](images/CopyAndDeleteConstructionNodes.png)

![](../images/line2.png)

##### `Step 6.`\|`ITB`| :small_orange_diamond: :small_blue_diamond:

Go into the **Event Graph** tab and click on an open space next to the **Event Begin Play** that is greyed out and press *paste*.

![paste nodes in event graph](images/PasteInEventGraphRm1.png)

![](../images/line2.png)

##### `Step 7.`\|`ITB`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

Adjust the position of the nodes to keep then neet. Attach the pin from **Event Begin Play** to the **Set Text** node. Now the **Begin Play** will only fire once when you run the game. So anything you connect to this pin will only run when you press the play button. Change the message to reflect that this will run when the **Begin Play** event is triggered. I put `I am the <br>BeginPlay Script node!`.  Notice that **<br>** is a carriage return (new line) that is the same syntax used in **HTML**.

![connect begin play](images/ConnectBeginPlayToSetTextExPins.png)

![](../images/line2.png)

##### `Step 8.`\|`ITB`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Press the <kbd>Compile</kbd> button until you get the green check mark.

![press compile](images/PressCompileRm1.png)

![](../images/line2.png)

##### `Step 9.`\|`ITB`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Go into the game and notice that it now says **Text**. This is the default value of that **Text** node that you could change in the blueprint if you wish.

![look at blueprint in game](images/image_02.png)

![](../images/line2.png)

##### `Step 10.`\|`ITB`| :large_blue_diamond:

Press the <kbd>Play</kbd> button and voila the text changes. When you stop the game, it goes back to its prior state of just having **Text** on the screen. So **Begin Play** only runs when you press play and all its changes reset when you stop the editor. The **Construction** script affects the editor when changes are made and the **Event Graph** only runs when the play button is pressed.  The begin play is the first thing that runs and it only runs **once**.

https://user-images.githubusercontent.com/5504953/192156895-d0db3923-c6f4-4c94-bd30-4962ed210a39.mp4


![](../images/line2.png)

##### `Step 11.`\|`ITB`| :large_blue_diamond: :small_blue_diamond: 

So **Begin Play** only runs when we run the game and it runs **ONCE**. Now we saw that the **Construction Script** ran when we compiled the blueprint. It also changes when that object changes in the level even before the game is run. Lets do one final demonstration of this.

Go back and open **BP_TextInConstructor** and add a **Random Integer in Range** node. Change the two values that the game will randomly generate to`20` and `50`. Change the **Make Litereal Text | Value** box `I am the <br>BeginPlay Script node! `. 

Add a **String | Append** node and connect **Make Literal Text** into the **A** of the **Append** node and the **Random Integer In Range | Return Value** to the **B** side of the **Append** node. This adds an integer to string conversion node for you. Make sure the is a space after the `!` in the This will concatonate the two strings together joining the message and the random number. 

Send the output of the **Append** node to the **Value** input pin in **Set Text** (it will add a **ToText(string)** conversion node for you).

https://user-images.githubusercontent.com/5504953/192158241-10e4607b-7094-4097-aec5-86e3c5d35802.mp4

(../images/line2.png)


##### `Step 12.`\|`ITB`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: 

Now you can change the random number and run that node every time you compile the blueprint or change that blueprint object in the editor. It only runs in these two conditions and will not run during the game. If you hit play that text will always be the same for as long as the game is running.

https://user-images.githubusercontent.com/5504953/192163148-c63ee5f2-422c-44d4-88ae-8af70d4573be.mp4

![](../images/line2.png)

##### `Step 13.`\|`ITB`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

Lets connect Unreal with our Perforce repository. Click on **Source Control | Change Source Control Settings...** and select the provider **Perforce**. Click on the <kbd>Accept Settings</kbd> button.

![connect to source control with git](images/connectToSource.png)

![](../images/line2.png)

##### `Step 14.`\|`ITB`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

Select the **File | Save All** then quit UE5.   Go to **P4V** and go the top project folder (the one that holds the `.uproject` file and **Content** folder) and press the <kbd>+Add</kbd> then <kbd>OK</kbd> button.  This makes sure any files that Unreal didn't add get added to source control. Press the <kbd>Submit</kbd> button and enter a message explaining the work done.  Press <kbd>Submit</kbd>.


![commit to source control in unreal](images/p4Submit.png)


![](../images/line.png)

<!-- <img src="https://via.placeholder.com/1000x100/45D7CA/000000/?text=Next Up - Collision Events"> -->

![next up next tile](images/banner.png)

| [previous](../constructor-begin/README.md#user-content-constructor--begin-play)| [home](../README.md#user-content-ue4-blueprints) | [next](../collision/README.md#user-content-collision-events)|
|---|---|---|
