<img src="https://via.placeholder.com/1000x4/45D7CA/45D7CA" alt="drawing" height="4px"/>

### Dynamically Alter Multiple Classes

<sub>[previous](../translation/README.md#user-content-translation) • [home](../README.md#user-content-ue4-blueprints) • [next](../multiple-actors-ii/README.md#user-content-dynamically-alter-multiple-classes-ii)</sub>

<img src="https://via.placeholder.com/1000x4/45D7CA/45D7CA" alt="drawing" height="4px"/>

Now you don't always have to assign the reference to the variable. You can access multiple instances of an object of the same class dynamically at run time as opposed to storing it in a variable at compile time. We can do this with a special node called **Get All Actors From Class**.

<br>

---


##### `Step 1.`\|`ITB`|:small_blue_diamond:

Add a `Blueprints | Room9` folder to your project. Press the <kbd>Add New</kbd> button and select **Blueprint Class**. Select type **Actor** class and call it `BP_LightbulbMulti`.

![add room 9 folder and add blueprint called BP_LightbulbMulti](images/AddBPRoom9.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 2.`\|`FHIU`|:small_blue_diamond: :small_blue_diamond: 

Open the new blueprint and *add* a new **Static Mesh** by *pressing* the **Add Component** button. Add a **Static Mesh** `Lightbulb`.

![add static mesh component](images/ExportStaticMeshRm9.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 3.`\|`ITB`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

*Rename* static mesh component to `Lightbulb` and *drag* it on its parent making it the root object. *Change* the scale to `10.0` on the **X,Y & Z** axis. Press the <kbd>Compile</kbd> button.

![rename and rescale lightbulb](images/ScaleLightbulb.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 4.`\|`ITB`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Scoot over to **Room 9** and *add* a whole bunch of lightbulbs in the room.

![add many lightbulbs to room](images/RenameBPLightbulbMultRm10.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 5.`\|`ITB`| :small_orange_diamond:

Open up **BP_LightbulbMulti**. Add a new component **Point Light** so that the bulbs actually light up the room. Make sure it is a child to the static mesh by dragging it over it. This way when you move the lightbult the light moves with it. *Press* the <kbd>Compile</kbd> button. Check that in the level it is casting light.

![add point light component](images/AddPointLight.jpg)

Now in game we have a shadow of the lightbulb which isn't realistic.  We want to kill the shadow.  Go to the **Blueprint** and select the **Lighting** component and `deselect` **Cast Shadows**.

![turn off cast shadow](images/TurnOffCastShadow.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 6.`\|`ITB`| :small_orange_diamond: :small_blue_diamond:

We need to add a dynamic materail to the **Construction Script**. To switch the light on and off we will need to turn the point light on and off as well as the material glow. Drag a reference of the **Lightbulb** static mesh onto the graph. Pull off the blue pin and select a **Create Dynamic Material Instance** node.

![add lightbulb and dynamic material to construction script](images/CreateDynamicMaterial.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 7.`\|`ITB`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

*Add* a new **Variable** and call it `DynamicMaterial`. *Choose* variable type **Material Instance Dynamic | Object Reference**. *Add* a **Tooltip** that says `Holds reference to material`. Put it in category `Lightbulb` and make it `Private`. *Drag* a **Set Dynamic Material** node to the graph and plug the **Return Value** from the **Create Dynamic Material Node** to the input pin of the **Set DynamicMaterial Variable**.

![add dynamci material variable and set it](images/SaveDynamicMaterialZ.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 8.`\|`ITB`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

*Connect* the execution pins from the **Construction** script node to the **Create Dynamic Material Instance** to the **Set Dynamic Material** nodes. Now the lightbulb's material with the glow is in **M_Glass**. *Select* the **Source Material** as `M_Glass` and set the **Element Index** to `1`.

![connect pins](images/image_08.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 9.`\|`ITB`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Press the **+** button next to **Functions** to add a new function. This allows us to put nodes in this blueprint that can be called from other objects. So intead of an internal event (BeginPlay or Tick) you can create your own function name and call it from another object.

Call this new function `SwitchLight`. We need to add an **Input** and call it `bTurnOn`. Make it type **boolean**. Without this there is no way for the function to know if we are turning the light **on** or **off**. Notice that this adds a pin to the **Switch Light** execution pin.

![add switch light function](images/SwitchLigthFunction.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 10.`\|`ITB`| :large_blue_diamond:

*Add* a **Branch Node** to the node graph. *Attach* the execution pins from **Switch Light** to **Turn On**.  Connect the  **Turn On** output pin to the **Condition** pin in the **Branch** Node. We will handle the turn on light logic from the **True** output pin and the turn off logic from the **False** pin.

![add branch node](images/AddBranchtoFunct.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 11.`\|`ITB`| :large_blue_diamond: :small_blue_diamond: 

*Click* on the **Point Light** in the **Components** menu. Lets look at the **Details** panel. A **Variable** called **Intensity** can be used to turn the acutal light on and off. We can set it to `0` when off and `5000` when on. Drag the **Point Light** to the graph and pull off its pin and select **Set Intensity** to change this value. Since this is for turning on set the **New Intensity** to `5000`.

![set intensity to 5000](images/SetPointLightIntensity.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>


##### `Step 12.`\|`ITB`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: 

Open up the **M_Glass** material. Look at what is going into the **Emissive Color** channel. We can use the **GlowMultiplier** Scalar Parameter to turn the glow on and off.

![m_glow material graph](images/GlowMultiplier.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 13.`\|`ITB`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

*Add* a reference to the **Dynamic Material** we just captured. *Pull off* the output pin and select **Set Scalar Parameter Value** and change the **Parameter Name** to `GlowMultiplier`. Make sure it is EXACTLY the same as the material. Set the **Value** to `6.0`. *Connect* the execution pins.

![set scalar parameter value](images/MultiplyGlow.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 14.`\|`ITB`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

Add a `Turn Light On` comment by highlighting the nodes and pressing the <kbd>C</kbd> key.

![add code comments](images/TurnLightOnComment.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 15.`\|`ITB`| :large_blue_diamond: :small_orange_diamond: 

*Copy and paste* all these nodes and change the comment to `Turn Light Off`. Set **New Intensity** and **Value** pins to `0.0`. *Connect* the **Set Intensity** execution pin to the **False** branch in the **Switch** node.

![copy and paste nodes for turning lights off](images/TurnOffBulbs.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 16.`\|`ITB`| :large_blue_diamond: :small_orange_diamond:   :small_blue_diamond: 

Lets test this function before moving forward. Go back to the **Event Graph** and add a function call by *right clicking* and adding a **Switch Light** node and connect it to begin play. *Play* the game with the **Turn On** boolean set to `false`. *Play* it in game and the lights should be off. Now do the same thing with the **Turn On** boolean set to `True`. *Run* the game the light should be on. Once you get this working *DELETE* the Switch Light node as we will be turning it on and off in another blueprint entirely.

![test light in game by switching Turn On off and on](images/TestTurnOnOffUnct.gif)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 17.`\|`ITB`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

In previous rooms we have put the trigger volume in the blueprint. In most cases we would have a trigger volum set in the level as it is always in a different place in the level and can sometimes control more than one blueprint. Go to **Volumes** and *drag* a **Trigger Volume **into the level. *Scale* it to add a box in front of the ligths so the player can walk into and out of it to trigger a lights on / lights off event.

![add trigger volume to level](images/UseLevelTriggerVolume.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 18.`\|`ITB`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Now do we get access to any object that is in the room? This is easy go to the game and select the **Trigger Volume** you just selected.

![select trigger volume in editor](images/BreakPinConnRm10.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 19.`\|`ITB`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Now since a blueprint can be used in any level and that this trigger is unique to this level, there is a special kind of blueprint. Everytime you have created a new Map or Level the game has automatically created a [Level Blueprint](https://docs.unrealengine.com/4.26/en-US/ProgrammingAndScripting/Blueprints/UserGuide/Types/LevelBlueprint/). This blueprint gives you access to all the insances included in that level in the editor. 

> A Level Blueprint is a specialized type of Blueprint that acts as a level-wide global event graph. Each level in your project has its own Level Blueprint created by default that can be edited within the Unreal Editor, however new Level Blueprints cannot be created through the editor interface.<br><br>Events pertaining to the level as a whole, or specific instances of Actors within the level, are used to fire off sequences of actions in the form of Function Calls or Flow Control operations. - UE4 manual

Press the **Blueprints** button and select **Open Level Blueprint**. Please note that these *do not* show up in your Content folder as they can't be deleted. Their location is essentially hidden.

![open level blueprint](images/NameFileBPRm10Switch.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 20.`\|`ITB`| :large_blue_diamond: :large_blue_diamond:

*Add* a new **Variable** and make it **Variable Type** of **BP Lightbulb Multi | Object Reference** and call it `Lightbulb Reference` and make it **Private**. What is the difference between **Object Reference** and **Class Reference**? The latter refers to the class as a whole and the **Object Reference** refers to each instance that is running. In this case we want to access each individual instance seperately. Next to **Variable** type *click* on the icon and select the grid to store an array of all lightbulbs.

![add reference to trigger volume in level bp](images/RefToLightbulbVariable.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 21.`\|`ITB`| :large_blue_diamond: :large_blue_diamond: :small_blue_diamond:

Now we need to get all the instances of the lightbulbs in the room. Add an **Event Begin Play** node. Right click and add a **Get All Actors of Class**. When you see a node that has **Get All** you know that it will most likely output an array of values.

![get all actors of class](images/DeleteLightReferenceVariable.jpg)

___


<img src="https://via.placeholder.com/1000x4/dba81a/dba81a" alt="drawing" height="4px" alt = ""/>

<img src="https://via.placeholder.com/1000x100/45D7CA/000000/?text=Next Up - Dynamically Alter Multiple Classes II">

<img src="https://via.placeholder.com/1000x4/dba81a/dba81a" alt="drawing" height="4px" alt = ""/>

| [previous](../translation/README.md#user-content-translation)| [home](../README.md#user-content-ue4-blueprints) | [next](../multiple-actors-ii/README.md#user-content-dynamically-alter-multiple-classes-ii)|
|---|---|---|
