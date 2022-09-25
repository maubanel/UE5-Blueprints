![](../images/line3.png)

### Collision Events

<sub>[previous](../constructor-begin-ii/README.md#user-content-constructor--begin-play-ii) • [home](../README.md#user-content-ue4-blueprints) • [next](../grouping-meshes/README.md#user-content-grouping-meshes)</sub>

![](../images/line3.png)

Now we can have a few types of collisions in **Unreal**. We can have a blocking collision that will stop two volumes from penetrating each other. Imagine a ball hitting a wall. We can also have a trigger collision where you can enter the collision volume and it will trigger a script. This is often when the player enters an invisible volume that they can't see. This is how we can access functionality in a script when a player is in a specific location in the level. This is the first type we will look at:

<br>

---

##### `Step 1.`\|`ITB`|:small_blue_diamond:

Create a new folder called `Room2` and put it in the **Blueprints** folder. Move the camera over to **Room 2** and press the <kbd>+ Add</kbd> button and select **Blueprint Class**.

![add blueprint class to blueprints folder](images/BlueprintClassRm2.png)

![](../images/line2.png)

##### `Step 2.`\|`FHIU`|:small_blue_diamond: :small_blue_diamond: 

We will be using this blueprint in a level so we will make it the base class of **Actor**.

![select actor class](images/InheritFromActorBlueprint.png)

![](../images/line2.png)

##### `Step 3.`\|`ITB`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Call it `BP_TextOnCollision`. *Drag* it into the room. In the **World Outliner** *drag* this newly created game object into the **Room 2** folder.

![drag BP_Text_OnCollision into room 2](images/NameAndPlaceBPRm2.png)

![](../images/line2.png)

##### `Step 4.`\|`ITB`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Double click the **blueprint**. Press the <kbd>+ Add</kbd> component button and select a **Text Render** component.

![add text render component](images/AddTextRenderComponentRm2.png)

![](../images/line2.png)

##### `Step 5.`\|`ITB`| :small_orange_diamond:

Now press **Add Component** again and this time we want a collision box. We can add multiple components to the same blueprints. If you type `collision` into the menu you will see three shapes: **Box**, **Sphere** and **Cylinder.** We will pick the **Box Collision**.

![add box collision component](images/CollisionComponentRm2.png)

![](../images/line2.png)

##### `Step 6.`\|`ITB`| :small_orange_diamond: :small_blue_diamond:

Rename the text component to `TextInRoom2`. Drag and drop this on top of the **DefaultSceneRoot** component. This will make the text box the root (parent) component. Make the **Text Render Color** more visible on a white background and change the **World Size** to `74` and make the text color **Green**.

![rename component and make world size 74 and recolor](images/RenameMakeParentRoot.png)

![](../images/line2.png)

##### `Step 7.`\|`ITB`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

With the **Box** component selected go to the **Details** panel and change the **Box Extent** to `600` on the **X**, `1400` on the **Y** and `200` on the **Z**. Also make sure the text element is at the rear of the collision box. Press the <kbd>Compile</kbd> button.

![change shape of collision box](images/ChangeBoxShape.png)

![](../images/line2.png)

##### `Step 8.`\|`ITB`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Now go into the game and reposition so the collision box is above the floor and centered in the room.

![reposition collisoin box in room](images/RepositionCollisionBoxRm2.png)

![](../images/line2.png)

##### `Step 9.`\|`ITB`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Go back to the **blueprint**. Make sure you are in the **Event Graph** tab. *Drag and drop* the **TextInRoom2** component into the scene graph. Left click the blue pin from this node and let go. This will now make sure that the context sensitive search will be items that are compatible with this reference. Start typing in **Text Render | Set Text** to get the **Set Text** node. COnnect the **Event Begin Play** execution pin to **Set Text**.

![drag text reference and add set text node](images/DragTextRefAndPinRm2.png)

![](../images/line2.png)

##### `Step 10.`\|`ITB`| :large_blue_diamond:

Left click and drag off the **Value** node from **Set Text**. Let go and start typing **Make Literal Text**. Select the **Make Literal Text** node and add the text: `You are inside the box!` to this node. Make sure the **Return Value** pin is connected to the **Value** pin on the **Set Text** node.

![add make literal text](images/DragOffValueNodeRm2.png)

![](../images/line2.png)

##### `Step 11.`\|`ITB`| :large_blue_diamond: :small_blue_diamond: 

Now the messages stays the same regardless as we have it connected to the **Begin Play**.  So it displays the message whether we are in or outside the collision volume.

https://user-images.githubusercontent.com/5504953/192165730-18fe4d05-aad9-480e-a5cf-b3be5580f7e9.mp4

![](../images/line2.png)


##### `Step 12.`\|`ITB`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: 

Since we added a **Collision** component the event graph shows a **Begin Overlap** event. This will trigger only one time when two objects overlap. In our case it will be the player's collision volume with this blueprint. It will only trigger a second time if the object leaves the collision volume then re-enters. Connect the execution pin from the **EventActorBeginOverlap** greyed out node to the **Set Text** node you just created.

![Connect set text execution pin to begin overlap](images/BeginOverlapPinConnectRm2.jpg)

![add text to literal text](images/MakeLiteralTextInsideBoxRm2.jpg)

![](../images/line2.png)

##### `Step 13.`\|`ITB`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

Run the game and move towards where the box is (we can't see it). You should see the text appear. It doesn't dissapear when you leave the box. Lets make some changes and improve this.

![you are inside the box text in game](images/RunGame.jpg)

![](../images/line2.png)

##### `Step 14.`\|`ITB`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

Go back to the blueprint and move the box component so the text is at the bottom left rear of the collision volume (behind if you like). Select the **Box** component and make sure the **Hidden In Game** box is `deselected`. Normally in a game we would hide our collision volumes, but for debug purposes lets set it so that we can see it for testing our work.

![unhide collision volume](images/ThreeChangesRm2.jpg)

![](../images/line2.png)

##### `Step 15.`\|`ITB`| :large_blue_diamond: :small_orange_diamond: 

Run the game and step into the box. The text is more obvious and better positioned. Make any necessary adjustments here. Now lets change the message when the player leaves the box.

![Run game and now you see the box](images/RunTheGameRm2B.jpg)

![](../images/line2.png)

##### `Step 16.`\|`ITB`| :large_blue_diamond: :small_orange_diamond:   :small_blue_diamond: 

*Copy and paste* the three nodes in the blueprint at the bottom.

![copy and paste three nodes in BP_TextOnCollision](images/CopyPasteThreeNodesRm2.jpg)

![](../images/line2.png)

##### `Step 17.`\|`ITB`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

Right click on a blank section of the scene graph. Type in and select **EventActorEndOverlap** node. This will only run once when a collision volume exits this blueprint collision volume. In this case it will be the players collision.

![add eventactorendoverlap node](images/ActorEndOverlapRm2.jpg)

![](../images/line2.png)

##### `Step 18.`\|`ITB`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Connect the execution pins from the **End Overlap** to the **Set Text**. Also change the **Value** to say `You are outside the box!`. Press the <kbd>Compile<kbd> button.

![change value to you rae inside the box and connect execution pins](images/ConnectPinsChangeMessageRm2.jpg)

![](../images/line2.png)

##### `Step 19.`\|`ITB`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Run the game and move inside and outside the collision volume and look at your blueprints being triggered.

![alt_text](images/CollisionText.gif)

![](../images/line2.png)

##### `Step 20.`\|`ITB`| :large_blue_diamond: :large_blue_diamond:

Lets look at the player blueprint quickly. Go to the **Blueprints** folder and double click **BP_PlayerCharacter**. Look at the components. It root component is a Capsule Collision component. This acts the same as the box component but is the shape of a capsule (a pill on its end). This is roughly the shape of a bipedal upright human. It also has a FirstPersonCamera where the head would be. Notice the collision volume goes above the player's virtual head. This is a first person controller so the Mesh is empty. It is just a collision volume with a camera that moves around. When this capsule overlaps the box collider in the blueprint it triggers the overlap events.

![root component of player](images/PlayerBPRm2.jpg)

![](../images/line2.png)

##### `Step 21.`\|`ITB`| :large_blue_diamond: :large_blue_diamond: :small_blue_diamond:

Run the game again but this time keep the blueprint tab open and out of the way. Zoom so you can see the entire node graph. When you play the game you can see the execution pin connectors light up when it is triggered. This shows you what is hapenning and is incredibly useful for debugging.

https://user-images.githubusercontent.com/5504953/132032366-f8bbba20-0f9d-456f-97f2-ad4af02cff25.mp4

![](../images/line2.png)

##### `Step 22.`\|`ITB`| :large_blue_diamond: :large_blue_diamond: :small_blue_diamond: :small_blue_diamond:

That's it for **Room 2**. *Press* **Save All** then go into **Source Control | Submit to Source Control...**, add a message that you have completed room 2 and press the <kbd>Submit</kbd> button. Now go to **GitHub Desktop** and **Push** changes to server. 

![save all, commit and push to github](images/Room2Github.jpg)

![](../images/line.png)

<!-- <img src="https://via.placeholder.com/1000x100/45D7CA/000000/?text=Next Up - Grouping Meshes"> -->

![next up next tile](images/banner.png)

![](../images/line.png)

| [previous](../constructor-begin-ii/README.md#user-content-constructor--begin-play-ii)| [home](../README.md#user-content-ue4-blueprints) | [next](../grouping-meshes/README.md#user-content-grouping-meshes)|
|---|---|---|
