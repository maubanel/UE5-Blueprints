![](../images/line3.png)

### Setting Up

<sub>[home](../README.md#user-content-ue4-blueprints) • [next](../constructor-begin/README.md#user-content-constructor--begin-play)</sub>

![](../images/line3.png)


Lets get going by setting up the project so we can start using blueprints.

<br>

---

| `required.software`\|`UE4 Lighting`| 
| :--- |
| :floppy_disk: &nbsp; &nbsp; You will need to install the latest version of _UE4 4.26.x_ by downloading the [Epic Games Launcher](https://www.epicgames.com/store/en-US/download). You will also need a [GitHub](https://github.com/) account which is free to sign up for as we will be using version control. You will also need a mac or PC that is powerful enough to run unreal. If you are on a PC you will have to download and install [git](https://git-scm.com/downloads) (on a mac it may prompt you to install git as well but you can do it through the terminal). We will also install [Github Desktop](https://desktop.github.com) as it provides a GUI interface so you don't have to worry about command line. Once git is installed you will also need to download and install the [Git LFS (Large File System)](https://git-lfs.github.com) as well for both PC and mac.  You will also need access to Maya 2020..\n\nLets make sure you can see hidden folders. On the PC follow these [Windows 10 Turn on Hidden Folders](https://support.microsoft.com/en-us/help/4028316/windows-view-hidden-files-and-folders-in-windows-10) directions. On the Mac it is a bit more involved so go and [turn on hidden folders on Mac](https://ianlunn.co.uk/articles/quickly-showhide-hidden-files-mac-os-x-mavericks).|

##### `Step 1.`\|`ITL`|:small_blue_diamond:

After you accept the [GitHub Classroom](https://classroom.github.com/a/HDRB55xp) invitation, go to the new **GitHub** repository and click on the green Code button and select open with **GitHub Desktop** then confirm that you will open in desktop then pick a directory and press the <kbd>Clone</kbd> button.

![github classroom invite to blueprints](images/IntroductionToBlueprintsClassroom.jpg)

![](../images/line2.png)

##### `Step 2.`\|`FHIU`|:small_blue_diamond: :small_blue_diamond: 

Go to your new GitHub repository and press the <kbd>Code</kbd> button and select **Open with GitHub Desktop**. Then you can then select a folder and **Clone** the project to your hard drive.

![accept and clone blueprints project](images/image_01.jpg)

![](../images/line2.png)

##### `Step 3.`\|`ITL`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

This will give you access to a folder called **UE4IntroToBlueprints** that will hold the UE4 project. Enter the folder double click the **UE4** project `IntroToBlueprints.uproject` to load it. Make sure you have Unreal 14.26.x installed.

![foler structure of blueprints project](images/InitialFolderStructure.jpg)

![](../images/line2.png)

##### `Step 4.`\|`ITL`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

The project should load up in the Room/Level **IntroToBlueprints1** room. Scoot the camera over to **Room 1**. You will also most likely see a dark room that has not been lit. You need to hit the <kbd>Build</kbd> button and wait for the lighting to build for the level. After this it should look normal again.

![room1 in game](images/IntroToBlueprints1Room.jpg)

![](../images/line2.png)

##### `Step 5.`\|`ITL`| :small_orange_diamond:

Go to the content browser and look at the folders that are provided. Go to the first **Blueprints** folder. You should see two files, one is a GameMode blueprint and the other is a character controller blueprint.

![character and gamemode blueprint](images/GameModeCharacterBlueprints.jpg)

![](../images/line2.png)

##### `Step 6.`\|`ITL`| :small_orange_diamond: :small_blue_diamond:

Go to the **Maps** folder and you should see two levels:

![maps folder showing two levels](images/ThreeRoomsMapFolder.jpg)

![](../images/line2.png)

##### `Step 7.`\|`ITL`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

You will now go to the **Materials** folder and I have provided some materials for these exercises. The **Supplied** folder has materials used for the room. The remaining ones will be used in blueprints you will be creating.

![contents of materials and supplied folder](images/MaterialsForBlueprints.jpg)

![](../images/line2.png)

##### `Step 8.`\|`ITL`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

In the **StaticMeshes** folder we have some models we will be using:

![contents of staticmeshes folder](images/StaticMeshes.jpg)

![](../images/line2.png)

##### `Step 9.`\|`ITL`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

And finally we have a **Textures** folder with the textures for the spotlight we will be using:

![content of textures folder](images/TexturesForBPs.jpg)

![](../images/line2.png)

##### `Step 10.`\|`ITL`| :large_blue_diamond:

Go into **Settings | Project Settings | Description** tab and fill in the requisite information:

![project settings description](images/ProjectSettingsDescription.jpg)

![](../images/line2.png)

##### `Step 11.`\|`ITL`| :large_blue_diamond: :small_blue_diamond: 

Go into the **Maps and Modes** tab. Notice the start up maps that we are booting to and meant to start with.

![default levels to load in maps and modes](images/MapsAndModes.jpg)

![](../images/line2.png)


##### `Step 12.`\|`ITL`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: 

Now select your default game mode: **BP_Gamemode**. This will select our character controller that we will be using:

![select BP_Gamemode](images/SelectDefaultGamemode.jpg)

![](../images/line2.png)

##### `Step 13.`\|`ITL`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

Go back to the **Blueprints** folder and press the <kbd>Add/Import</kbd> button and select **New Folder**. Call it `Room1`.

![add Room1 folder to Blueprints](images/NewFolderInBlueprints.jpg)

![](../images/line2.png)

![](../images/line.png)

<!-- <img src="https://via.placeholder.com/1000x100/45D7CA/000000/?text=Next Up - Next Up - Constructor and Begin Play"> -->

![next up next tile](images/banner.png)

![](../images/line.png)

| [home](../README.md#user-content-ue4-blueprints) | [next](../constructor-begin/README.md#user-content-constructor--begin-play)|
|---|---|
