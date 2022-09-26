![](../images/line3.png)

### Grouping Meshes

<sub>[previous](../collision/README.md#user-content-collision-events) • [home](../README.md#user-content-ue4-blueprints) • [next](../dynamic-materials/README.md#user-content-dynamic-materials)</sub>

![](../images/line3.png)

Now **blueprints** are not just for logic. We can use them to create a more complex object with multiple meshes and components and save them as one blueprint. Then you can make multiple instances of them and they will be replicated. You can also build it in the game world first, then create a bluprint after. Lets create a spotlight and see how this works.

<br>

---

##### `Step 1.`\|`ITB`|:small_blue_diamond:

Go to **Room 3** and go to the **StaticMeshes** folder. Drag the **spotlight_bracket** into the room. Position it so it faces the front left of the room.

![drag spotlight in room 3](images/DragBracketRm3.png)

![](../images/line2.png)

##### `Step 2.`\|`FHIU`|:small_blue_diamond: :small_blue_diamond: 

Move the object in the **World Outliner** into the **Room 3** folder. Then press the **Add Component** button.

![move to room 3 folder and add component](images/MoveToRoom3.png)

![](../images/line2.png)

##### `Step 3.`\|`ITB`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Select another **Static Mesh** component.

![add another static mesh component](images/AddSecondStaticMeshRm3.png)

![](../images/line2.png)

##### `Step 4.`\|`ITB`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Assign the **spotlight_lamp** mesh to this component

![assing lamp to static mesh](images/AssignLampToStaticMeshRm3.png)

![](../images/line2.png)

##### `Step 5.`\|`ITB`| :small_orange_diamond:

Add a third static mesh component by pressing the <kbd>Add Component</kbd> button:

![add component](images/Assign3rdStaticMeshComponent.jpg)

![](../images/line2.png)

##### `Step 6.`\|`ITB`| :small_orange_diamond: :small_blue_diamond:

Assign the **Lightbulb** static mesh. Rotate lightbulb so that the bulb faces down and move it to the proper location.

![assign lightbulb static mesh](images/AssignLightbulbRm3.png)

![](../images/line2.png)

##### `Step 7.`\|`ITB`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:



![rotate lightbulb](images/image_07.jpg)

![](../images/line2.png)

##### `Step 8.`\|`ITB`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Rename the **Actor** to `Spotlight`.

![rename actor to spotlight](images/RenameActorToSpotlightRm3.png)

![](../images/line2.png)

##### `Step 9.`\|`ITB`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Add another component but this time an actual Spotlight so it can project an in game spotlight. Pressing <kbd>Add Component</kbd> button then select **Spot Light**.

![add spot light component](images/AddSpotLightComponent.png)

![](../images/line2.png)

##### `Step 10.`\|`ITB`| :large_blue_diamond:

Create a new folder called **Room3** in the **Blueprints** folder. Now make sure that your **Spotlight** is selected in the **Outliner**. Then press the <kbd>Convert to Blueprint</kbd> button to turn this from a level instance to a reusable blueprint. Add it to the **Blueprints | Room3** folder and call it `BP_Spotlight`. Make sure **New Subclass** is selected then press the <kbd>Select</kbd> button. 

![turn mesh into blueprint](images/TurnSpotlightIntoBPRm3.jpg)

![](../images/line2.png)

##### `Step 11.`\|`ITB`| :large_blue_diamond: :small_blue_diamond: 

Open the **BP_Spotlight** blueprint and select the **Spotlight**. You will see that its rotation may not match the light.

![rotate spotlight to match light](images/RotateLightRm3.jpg)

![](../images/line2.png)


##### `Step 12.`\|`ITB`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: 

Make sure it is rotated in the same direction as the lamp.

![match direction with rotation](images/RotateLight.jpg)

![](../images/line2.png)

##### `Step 13.`\|`ITB`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

Now make sure that the parent child relationship is correct.  We want the **SpotlightLamp** to be at the top with a child of **Lightbulb** and grand child of **Spot Light**. This way when you move or rotate the object everything moves with it.

![proper parent child hiearchy](images/ParentChild.jpg)

Select the **Lamp** component and rotate the lamp so that it doesn't point straight down. Tune it to your liking:

![rotate lamp to your liking](images/RotateLampToOffsetIt.jpg)

![](../images/line2.png)

##### `Step 14.`\|`ITB`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

Select the **Spotlight** then set the light color to your preference. I picked green.

![change spotlight color](images/ChangeSpotlightColor.jpg)

![](../images/line2.png)

##### `Step 15.`\|`ITB`| :large_blue_diamond: :small_orange_diamond: 

Check the lamp out in game. Make sure the light bulb mesh is not casting a shadow from the light. If it is *move* the **Spot Light** component further away from the light bulb and check in game to where it no longer is shadowed or occluded by the light bulb mesh.

![check in game that light is correct](images/CheckInGameLightBehindBulb.jpg)

![](../images/line2.png)

##### `Step 16.`\|`ITB`| :large_blue_diamond: :small_orange_diamond:   :small_blue_diamond: 

Now by having it as a blueprint I can just drop it in the room multiple times and rotate it in different direcions. I have a game object that I can instance as much as I want with the functionality I need!

![drop multiple blueprints in room](images/DropBlueprintInMultipleLocations.jpg)

![](../images/line2.png)

##### `Step 17.`\|`ITB`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

Now this is what it could look like in game.

![final lights game](images/InGameFinalLook.jpg)

![](../images/line2.png)

##### `Step 18.`\|`ITB`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

That's it for **Room 3**. Press **Save All** then go into **Source Control | Submit to Source Control...**, add a message that you have completed room 3 and press the <kbd>Submit</kbd> button. Now go to **GitHub Desktop** and **Push** changes to server. 

![save, commit and push to github](images/GItHubRoom3.jpg)

![](../images/line.png)

<!-- <img src="https://via.placeholder.com/1000x100/45D7CA/000000/?text=Next Up - Dynamic Materials"> -->

![next up next tile](images/banner.png)

![](../images/line.png)

| [previous](../collision/README.md#user-content-collision-events)| [home](../README.md#user-content-ue4-blueprints) | [next](../dynamic-materials/README.md#user-content-dynamic-materials)|
|---|---|---|
