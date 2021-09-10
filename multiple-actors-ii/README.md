<img src="https://via.placeholder.com/1000x4/45D7CA/45D7CA" alt="drawing" height="4px"/>

### Dynamically Alter Multiple Classes II

<sub>[previous](../multiple-actors/README.md#user-content-dynamically-alter-multiple-classes) • [home](../README.md#user-content-ue4-blueprints) • [next](../interface/README.md#user-content-communicate-through-interface)</sub>

<img src="https://via.placeholder.com/1000x4/45D7CA/45D7CA" alt="drawing" height="4px"/>

Controlling multiple actors through level blueprints continued...

<br>

---


##### `Step 1.`\|`ITB`|:small_blue_diamond:

Connect the execution pins from **Begin Play** to **Get All Actors of Class**. Select the actor you want to get from the level for the **Get All Actors From Class | Actor Class** to`BP_LightbulbMulti`. Now drag a copy of **Set Lightbulb Reference** and connect the output array pin to the input array pin of these nodes as shown. Connect the execution pin from **Get All Actors of Class** to **Set Lightbulb** nodes.

![add set lightbulb ref to graph](images/SayYesRm10.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 2.`\|`FHIU`|:small_blue_diamond: :small_blue_diamond: 

Make sure you still have the trigger volume selected in the editor. Right click on the graph and see that we can now access events to this game object. Select **Add Event for Trigger Volume 1 | Collision | Add on Actor Begin Overlap** AND a **Add Event for Trigger Volume 1 | Collision | Add on Actor End Overlap** node. This will trigger the nodes when an actor enters and leaves the volume.

![add begin and end overlap event types](images/GetAllActorsOfClass.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 3.`\|`ITB`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

*Add* a **Flip Flop** node to the chart. This node when triggered toggles between true and false. Connect it to both the **Overlap** nodes. This way the first time you enter the volue it will switch on, then when you leave swtich off. This will continue this behavior during the game. What will happen is that the **IsA** boolean on the **Flip Flop** pin will change from **True** to **False** and back.

![add flip flop node](images/ActorClassBPSelectRm10.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 4.`\|`ITB`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Add a comment by pressing the <kbd>C</kbd> and call it `Toggle`.

![add code comments](images/ActorArrayOut.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 5.`\|`ITB`| :small_orange_diamond:

*Drag* a copy of the **Get RefToLightbulbs** variable onto the graph.

![add ref to lightbulbs to graph](images/DragRefToLightbulbs.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 6.`\|`ITB`| :small_orange_diamond: :small_blue_diamond:

How do we get access to each instance of each lightbulb in the array and not the entire array? We use a **For Each** loop. *Right click* and add a **For Each Loop** to the graph.

![add for each loop](images/ConnectActorToForEachRm10.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 7.`\|`ITB`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

*Connect* the **A** and **B** execution pins from the **Flip Flop** node to the **E**xec pin in the **For Each Loop** node. *Connect* the output of the **RefToLightbulbs** node to the **Array** input pin in the **For Each Loop**.

![connect array to for each loop pins](images/ArrayElementSwitchLightRm10.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 8.`\|`ITB`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

*Pull off* of the **Array Element** pin and trigger the **Switch Light** function in each light. Connect the output of the **Flip Flop | Is A** node to the **Switch Light** node's **Is On** pin. Connect the execution pin from **Loop Body** to **Switch Light**.

*Press** the <kbd>Compile</kbd> button.

**IsA** gives the current state.  So every time the **Flip Flop** node is triggered this goes between **True** and **False**.  **IsA** outputs the switched state (so if it was **True** before and when triggered becomes **False**).

![connect isA to Turn On](images/SwitchLightOnOff.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 9.`\|`ITB`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Go to **BP_LightbulbMulti** and the **Event Graph** *add* a **Switch Light** node and set it to `false` so that the lights ALWAYS start turned off. *Press* the <kbd>Compile</kbd> button.

![call switch light in begin play with lights off](images/image_09.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 10.`\|`ITB`| :large_blue_diamond:

Now run the game and enter and leave the room. The lights should toggle on and off.

![run game and trigger lights on and off](images/TurnOnOffLights.gif)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 11.`\|`ITB`| :large_blue_diamond: :small_blue_diamond: 

That's it for **Room 9**. *Press* **Save All** and update **Github** by committing and pushing all the changes made. Next up we will be using a broadcast event to access the on off switch on classes of different types.

![save, commit and push to github](images/Room9GitHub.jpg)

___


<img src="https://via.placeholder.com/1000x4/dba81a/dba81a" alt="drawing" height="4px" alt = ""/>

<img src="https://via.placeholder.com/1000x100/45D7CA/000000/?text=Next Up - Communicate Through Interface">

<img src="https://via.placeholder.com/1000x4/dba81a/dba81a" alt="drawing" height="4px" alt = ""/>

| [previous](../multiple-actors/README.md#user-content-dynamically-alter-multiple-classes)| [home](../README.md#user-content-ue4-blueprints) | [next](../interface/README.md#user-content-communicate-through-interface)|
|---|---|---|
