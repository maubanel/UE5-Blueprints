![](../images/line3.png)

### Dynamically Alter Multiple Classes II

<sub>[previous](../multiple-actors/README.md#user-content-dynamically-alter-multiple-classes) • [home](../README.md#user-content-ue4-blueprints) • [next](../interface/README.md#user-content-communicate-through-interface)</sub>

![](../images/line3.png)

Controlling multiple actors through level blueprints continued...

<br>

---

##### `Step 1.`\|`ITB`|:small_blue_diamond:

Now do we get access to any object that is in the room? This is easy go to the game and select the **Trigger Volume** you just selected. Make sure you still have the trigger volume selected in the editor. Right click on the graph and see that we can now access events to this game object. Select **Add Event for Trigger Box 0 | Collision | Add on Actor Begin Overlap** AND a **Add Event for Trigger Box 0 | Collision | Add on Actor End Overlap** node. This will trigger the nodes when an actor enters and leaves the volume.

![add begin and end overlap event types](images/GetAllActorsOfClass.png)

![](../images/line2.png)

##### `Step 2.`\|`FHIU`|:small_blue_diamond: :small_blue_diamond: 


So now you should have two events for when the player enters and leaves the volume.

![two volume triggered events](images/bothEvents.png)

![](../images/line2.png)

##### `Step 3.`\|`ITB`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

*Add* a new **Variable** and make it **Variable Type** of **BP_LightbulbMulti | Object Reference** and call it `LightbulbReferences` and make it **Private**. What is the difference between **Object Reference** and **Class Reference**? The latter refers to the class as a whole and the **Object Reference** refers to each instance that is running. In this case we want to access each individual instance seperately. Next to **Variable** type *click* on the **icon** and select the **Grid** icon to store an **array** of all lightbulbs. The array type stores a list of objects of the same type.  So for **LightbulbReference** it will store a list of all the **BP_LightbulbMulti**'s in the level.  Add a **Description** saying `Holds reference to all the lightbulbs in Room 9`. 

https://user-images.githubusercontent.com/5504953/193477461-7465cd3c-1878-4e4b-91e3-4d9181c15ee6.mp4

![](../images/line2.png)

##### `Step 4.`\|`ITB`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Now we need to get all the instances of the lightbulbs in the room. Add an **Event Begin Play** node. Right click and add a **Get All Actors of Class**. When you see a node that has **Get All** you know that it will most likely output an array of values. In **Actor Class** select `BP_LightbulbMulti`. Connect the execution pins from **Begin Play** to **Get All Actors of Class**.

![get all actors of class](images/DeleteLightReferenceVariable.png)


![](../images/line2.png)

##### `Step 5.`\|`ITB`| :small_orange_diamond:

Now drag a copy of **Set Lightbulb Reference** and connect the output array pin to the input array pin of these nodes as shown. Connect the execution pin from **Get All Actors of Class** to **Set Lightbulb** nodes. Connect the execution pin from **Get All Actors from Class** to the **Set Lightbulb Reference** node.

![add set lightbulb ref to graph](images/SayYesRm10.png)

![](../images/line2.png)

##### `Step 7.`\|`ITB`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

Clean up your node graph and add a comment indicating that we are getting a reference to all the actors in the scene.

![clean up node chart and add comment](images/addComment.png)

![](../images/line2.png)

##### `Step 6.`\|`ITB`| :small_orange_diamond: :small_blue_diamond:


*Add* a **Flip Flop** node to the chart. This node when triggered toggles between true and false. Connect it to both the **Overlap** nodes. This way the first time you enter the volue it will switch on, then when you leave swtich off. This will continue this behavior during the game. What will happen is that the **IsA** boolean on the **Flip Flop** pin will change from **True** to **False** and back.

![add flip flop node](images/ActorClassBPSelectRm10.png)


![](../images/line2.png)

##### `Step 8.`\|`ITB`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Add a comment by pressing the <kbd>C</kbd> and call it `Toggle Lights`. *Drag* a copy of the **Get RefToLightbulbs** variable onto the graph.

![add code comments](images/ActorArrayOut.png)

![](../images/line2.png)

##### `Step 9.`\|`ITB`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

How do we get access to each instance of each lightbulb in the array and not the entire array? We use a **For Each Loop**. *Right click* and add a **For Each Loop** to the graph. *Connect* the **A** and **B** execution pins from the **Flip Flop** node to the **E**xec pin in the **For Each Loop** node. *Connect* the output of the **RefToLightbulbs** node to the **Array** input pin in the **For Each Loop**.

![add for each loop](images/ConnectActorToForEachRm10.png)

![](../images/line2.png)

##### `Step 10.`\|`ITB`| :large_blue_diamond:

*Pull off* of the **Array Element** pin and trigger the **Switch Light** function in each light.  This for each loop goes through each instance and calls the **Switch Light** function.

![call switch light](images/callSwitchLight.png)

![](../images/line2.png)

##### `Step 11.`\|`ITB`| :large_blue_diamond: :small_blue_diamond: 

Connect the output of the **Flip Flop | Is A** node to the **Switch Light** node's **Is On** pin. Connect the execution pin from **Loop Body** to **Switch Light**. *Press** the <kbd>Compile</kbd> button. **IsA** gives the current state.  So every time the **Flip Flop** node is triggered this goes between **True** and **False**.  **IsA** outputs the switched state (so if it was **True** before and when triggered becomes **False**).

![connect is a to switch light](images/connectSL.png)

![](../images/line2.png)


##### `Step 12.`\|`ITB`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: 

Go back to **BP_LightbulbMulti** and make sure that the **Begin Play** switches the lights off by default.  So **Turn On** should be `false`.

![turn off light in begin play](images/defaultFalse.png)

![](../images/line2.png)

##### `Step 13.`\|`ITB`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

*Press* the <kbd>Play</kbd> button and run into the volume, it should trigger the lights to turn on.  Then leave the collision volume and it kills all the lights.  The nice thing is we have one collision volumes that controls all 20 lights.

https://user-images.githubusercontent.com/5504953/193478516-fd17a586-e420-4272-aff7-9d1d0b92a875.mp4

![](../images/line2.png)

##### `Step 14.`\|`ITB`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

 Move and sure all the Lightbulbs and the Trigger Volume are in the **Room 9** folder in the **Outliner**.

![save all and submit to perforce in P4V](images/cleanUp.png)

![](../images/line2.png)

##### `Step 15.`\|`ITB`| :large_blue_diamond: :small_orange_diamond: 

Select the **File | Save All** then press the <kbd>Revision Control</kbd> button and select **Submit Content**.  If you are prompted, select **Check Out** for all items that are not checked out of source control. Update the **Changelist Description** message and with the latest changes. Make sure all the files are correct and press the <kbd>Submit</kbd> button. A confirmation will pop up on the bottom right with a message about a changelist was submitted with a commit number. Quit Unreal and make sure your **Pending** tab in **P4V** is empty. **Submit** any work that is still in the editor.

![save all and submit to perforce in P4V](images/submitP4.png)

![](../images/line2.png)

##### `Step 16.`\|`ITB`| :large_blue_diamond: :small_orange_diamond:   :small_blue_diamond: 

Sometimes not all files get submitted to Unreal especially for files that don't show up in the editor.  It is good practice one you submit in **Unreal** and quit the game to right click on the top most project folder and select **Reconcile Offline Work...**.

This will either give a message saying ther is nothing to reconcile or bring up a tab.  Make sure that these are **NOT** files in the **Intermediate** and **Saved** folders as these should be ignored from the `.p4ignore`.

If the files are in **Content** or **Configuration** then press the <kbd>Reconcile</kbd> button.  Then submit the changes with a message and press the <kbd>Submit</kbd> button.

![reconcile offline work](images/reconcile.png) 

![](../images/line.png)

<!-- <img src="https://via.placeholder.com/1000x100/45D7CA/000000/?text=Next Up - Communicate Through Interface"> -->

![next up next tile](images/banner.png)

![](../images/line.png)

| [previous](../multiple-actors/README.md#user-content-dynamically-alter-multiple-classes)| [home](../README.md#user-content-ue4-blueprints) | [next](../interface/README.md#user-content-communicate-through-interface)|
|---|---|---|
