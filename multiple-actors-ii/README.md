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

*Add* a new **Variable** and make it **Variable Type** of **BP_LightbulbMulti | Object Reference** and call it `LightbulbReferences` and make it **Private**. What is the difference between **Object Reference** and **Class Reference**? The latter refers to the class as a whole and the **Object Reference** refers to each instance that is running. In this case we want to access each individual instance seperately. Next to **Variable** type *click* on the **icon** and select the **Grid** icon to store an **array** of all lightbulbs.

https://user-images.githubusercontent.com/5504953/193477461-7465cd3c-1878-4e4b-91e3-4d9181c15ee6.mp4

![](../images/line2.png)

##### `Step 4.`\|`ITB`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Now we need to get all the instances of the lightbulbs in the room. Add an **Event Begin Play** node. Right click and add a **Get All Actors of Class**. When you see a node that has **Get All** you know that it will most likely output an array of values. In **Actor Class** select `BP_LightbulbMulti`.

![get all actors of class](images/DeleteLightReferenceVariable.png)


![](../images/line2.png)

##### `Step 5.`\|`ITB`| :small_orange_diamond:

Once you get this working *DELETE* the Switch Light node as we will be turning it on and off in another blueprint entirely.

Connect the execution pins from **Begin Play** to **Get All Actors of Class**. Select the actor you want to get from the level for the **Get All Actors From Class | Actor Class** to`BP_LightbulbMulti`. Now drag a copy of **Set Lightbulb Reference** and connect the output array pin to the input array pin of these nodes as shown. Connect the execution pin from **Get All Actors of Class** to **Set Lightbulb** nodes.

![add set lightbulb ref to graph](images/SayYesRm10.jpg)

*Add* a **Flip Flop** node to the chart. This node when triggered toggles between true and false. Connect it to both the **Overlap** nodes. This way the first time you enter the volue it will switch on, then when you leave swtich off. This will continue this behavior during the game. What will happen is that the **IsA** boolean on the **Flip Flop** pin will change from **True** to **False** and back.

![add flip flop node](images/ActorClassBPSelectRm10.jpg)


Add a comment by pressing the <kbd>C</kbd> and call it `Toggle`.

![add code comments](images/ActorArrayOut.jpg)

*Drag* a copy of the **Get RefToLightbulbs** variable onto the graph.

![add ref to lightbulbs to graph](images/DragRefToLightbulbs.jpg)

![](../images/line2.png)

##### `Step 6.`\|`ITB`| :small_orange_diamond: :small_blue_diamond:

How do we get access to each instance of each lightbulb in the array and not the entire array? We use a **For Each** loop. *Right click* and add a **For Each Loop** to the graph.

![add for each loop](images/ConnectActorToForEachRm10.jpg)

![](../images/line2.png)

##### `Step 7.`\|`ITB`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

*Connect* the **A** and **B** execution pins from the **Flip Flop** node to the **E**xec pin in the **For Each Loop** node. *Connect* the output of the **RefToLightbulbs** node to the **Array** input pin in the **For Each Loop**.

![connect array to for each loop pins](images/ArrayElementSwitchLightRm10.jpg)

![](../images/line2.png)

##### `Step 8.`\|`ITB`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

*Pull off* of the **Array Element** pin and trigger the **Switch Light** function in each light. Connect the output of the **Flip Flop | Is A** node to the **Switch Light** node's **Is On** pin. Connect the execution pin from **Loop Body** to **Switch Light**.

*Press** the <kbd>Compile</kbd> button.

**IsA** gives the current state.  So every time the **Flip Flop** node is triggered this goes between **True** and **False**.  **IsA** outputs the switched state (so if it was **True** before and when triggered becomes **False**).

![connect isA to Turn On](images/SwitchLightOnOff.jpg)

![](../images/line2.png)

##### `Step 9.`\|`ITB`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Go to **BP_LightbulbMulti** and the **Event Graph** *add* a **Switch Light** node and set it to `false` so that the lights ALWAYS start turned off. *Press* the <kbd>Compile</kbd> button.

![call switch light in begin play with lights off](images/image_09.jpg)

![](../images/line2.png)

##### `Step 10.`\|`ITB`| :large_blue_diamond:

Now run the game and enter and leave the room. The lights should toggle on and off.

![run game and trigger lights on and off](images/TurnOnOffLights.gif)

![](../images/line2.png)

##### `Step 11.`\|`ITB`| :large_blue_diamond: :small_blue_diamond: 

That's it for **Room 9**. Press **Save All** and update **Github** by **committing** and **pushing** all the changes made using **Unreal Source Control** and **GitHub Desktop**. 

![save, commit and push to github](images/Room9GitHub.jpg)

![](../images/line.png)

<!-- <img src="https://via.placeholder.com/1000x100/45D7CA/000000/?text=Next Up - Communicate Through Interface"> -->

![next up next tile](images/banner.png)

![](../images/line.png)

| [previous](../multiple-actors/README.md#user-content-dynamically-alter-multiple-classes)| [home](../README.md#user-content-ue4-blueprints) | [next](../interface/README.md#user-content-communicate-through-interface)|
|---|---|---|
