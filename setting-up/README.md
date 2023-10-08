![](../images/line3.png)

### Setting Up

<sub>[home](../README.md#user-content-ue4-blueprints) • [next](../constructor-begin/README.md#user-content-constructor--begin-play)</sub>

![](../images/line3.png)

Lets get going by setting up the project so we can start using blueprints.


---

| `required.software`\|`UE4 Lighting`| 
| :--- |
| :floppy_disk: &nbsp; &nbsp; You will need to install the latest version of _UE5 5.2.X_ by downloading the [Epic Games Launcher](https://www.epicgames.com/store/en-US/download). You will also need a [P4V](https://www.perforce.com/downloads/helix-visual-client-p4v) account which is free to sign up for as we will be using version control. Lets make sure you can see hidden folders. On the PC follow these [Windows 10 Turn on Hidden Folders](https://support.microsoft.com/en-us/help/4028316/windows-view-hidden-files-and-folders-in-windows-10) directions.|

##### `Step 1.`\|`ITL`|:small_blue_diamond:

In your **Perforce** folder you should see a folder called **UE5-Intro-To-Blueprints**. Double click `UE5IntroToBlueprints.uproject` to load up **Unreal**.

![download starter project and unzip](images/downloadExtract.png)

![](../images/line2.png)

##### `Step 2.`\|`FHIU`|:small_blue_diamond: :small_blue_diamond: 

You should make sure the player start is in front and facing to **Room 1**.

![change name and delete files](images/changeNameDel.png)

![](../images/line2.png)

##### `Step 3.`\|`ITL`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Now the player is similar to the one created in the animation walk through.  It is a first person player so no character (just a camera) and there is an **IA_Look** input action.  This action affects the camera so you can look around with the mouse. These are assigned butttons in the **IMC_Default** input controller.

![drag UE5-Intro-To-Blueprints to p4 workspace](images/workspaceFolder.png)

![](../images/line2.png)

##### `Step 4.`\|`ITL`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

In the **Blueprints | Game** folder we have two blueprints.  One is the first person characater you are controlling **BP_PlayerCharacter** and **BP_Gamemode** which uses this character as the default pawn.

![add .p4ignore to workspace](images/addP4Ignore.png)

![](../images/line2.png)

##### `Step 5.`\|`ITL`| :small_orange_diamond:

Open up **P4V** and select the folder **UE5-Intro-To-Blueprints**.  Press the <kbd>+ Add</kbd> button. Leave it on the **Default** changelist and press the <kbd>OK</kbd> button.

![add new files from blueprints project to depot](images/addToP4.png)


![](../images/line2.png)

##### `Step 6.`\|`ITL`| :small_orange_diamond: :small_blue_diamond:

Press the <kbd>Submit</kbd> button and enter a message.  Then in the pop-up press the <kbd>Submit</kbd> button.

![submit p4 changelist](images/submit.png)

![](../images/line2.png)

##### `Step 7.`\|`ITL`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

In **P4V** double click **UE5Blueprints**.

![in P4V double click UE5Blueprints](images/startGame.png)

![](../images/line2.png)

##### `Step 8.`\|`ITL`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

The project should load up in the Room/Level **IntroToBlueprints1** room. Scoot the camera over to **Room 1**. 

![room1 in game](images/room1.png)

![](../images/line2.png)

##### `Step 9.`\|`ITL`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Go to the content browser and look at the folders that are provided. Go to the first **Blueprints | Game** folder. You should see two files, one is a GameMode blueprint and the other is a character controller blueprint. The gamemode is used by **Project Settings** to load up the character in both levels in the game.

![character and gamemode blueprint](images/blueprintsFolder.png)


Go to the **Maps** folder and you should see two levels:

![maps folder showing two levels](images/levels.png)

![](../images/line2.png)

##### `Step 10.`\|`ITL`| :large_blue_diamond:

You will now go to the **Materials | Supplied** folder and I have provided some materials for these exercises. T

![contents of materials and supplied folder](images/materials.png)

![](../images/line2.png)

##### `Step 11.`\|`ITL`| :large_blue_diamond: :small_blue_diamond: 

In the **StaticMeshes | Supplied** folder we have some models we will be using for the exercise including the environment we are in.

![contents of staticmeshes folder](images/meshes.png)

![](../images/line2.png)

##### `Step 12.`\|`ITL`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: 

And finally we have a **Textures** folder with the textures for the spotlight we will be using:

![content of textures folder](images/textures.png)

![](../images/line2.png)

##### `Step 13.`\|`ITL`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

Go into **Settings | Project Settings | Description** tab and fill in the requisite information, especially the license file.  I use the [MIT License](https://www.google.com/search?client=safari&rls=en&q=mit+open+source+licnese+text&ie=UTF-8&oe=UTF-8).

![project settings description](images/projectDescription.png)

![](../images/line2.png)

##### `Step 14.`\|`ITB`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

Go into the **Maps and Modes** tab. Notice the start up maps that we are booting to and meant to start with.

![default levels to load in maps and modes](images/mapsAndModes.png)

![](../images/line2.png)

##### `Step 15.`\|`ITB`| :large_blue_diamond: :small_orange_diamond: 

Go back to the **Blueprints** folder and press the <kbd>Add/Import</kbd> button and select **New Folder**. Call it `Room1`.

![add Room1 folder to Blueprints](images/bpRoom1.png)

![](../images/line2.png)

##### `Step 16.`\|`ITB`| :large_blue_diamond: :small_orange_diamond:   :small_blue_diamond: 
Select the **File | Save All** then quit UE5.   Go to **P4V** and go the top project folder (the one that holds the `.uproject` file and **Content** folder) and press the <kbd>+Add</kbd> then <kbd>OK</kbd> button.  This makes sure any files that Unreal didn't add get added to source control. Press the <kbd>Submit</kbd> button and enter a message explaining the work done.  Press <kbd>Submit</kbd>.

![save all and submit to perforce in P4V](images/submitP4.png)

![](../images/line.png)

<!-- <img src="https://via.placeholder.com/1000x100/45D7CA/000000/?text=Next Up - Next Up - Constructor and Begin Play"> -->

![next up next tile](images/banner.png)

![](../images/line.png)

| [home](../README.md#user-content-ue4-blueprints) | [next](../constructor-begin/README.md#user-content-constructor--begin-play)|
|---|---|
