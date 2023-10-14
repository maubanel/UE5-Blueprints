![](../images/line3.png)

### Translation II

<sub>[previous](../translation/README.md#user-content-translation) • [home](../README.md#user-content-ue5-blueprints) • [next](../multiple-actors/README.md#user-content-dynamically-alter-multiple-classes)</sub>

![](../images/line3.png)

Lets finish up translating the cube on the Y and X axis.

<br>

---

##### `Step 1.`\|`ITB`|:small_blue_diamond:
*Copy and paste* the entire section below it. Change the **Comment** to `Translate on Y`.  Right click on the **bTranslateOnX** node and select **Replace variable 'bTranslateOnX' with... | bTranslateOnY`**.  This will change it to the **Y** axis. 

![copy](images/copyPasteXtoY.png)

![](../images/line2.png)

##### `Step 2.`\|`ITB`|:small_blue_diamond: :small_blue_diamond: 

Connect the **Lerp** from the Y section to **SetRelativeLocatoin | New Location Y**. Connect the **Alpha** of the **Lerp** to the **SIN** node.Connect the output of the **Sequence | Then 1** pin to the **Branch** node hooked up to **bTranslateOnY**.

![connect pins](images/connectY.png)

![](../images/line2.png)

##### `Step 3.`\|`ITB`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

In the editor change it to only **Translate on Z** as `true` and the **CmOfTravel** to `4`. *Press* the <kbd>Play</kbd> button to see the box move in and out of the screen.

https://user-images.githubusercontent.com/5504953/193455503-434b6730-87b7-4d61-861b-2abda5624914.mp4

*Copy and paste* all the nodes from the **Translate On Z** section again. Change the **Comment** to `Translate on X`. Also *delete* the **Translate On Z** getter in the graph and drag and drop **Translate On X**. Change the connecdtion from the **Multiplication** node to **Delta Locaion on X**.

![copy and paste to translate on x](images/translateOnX.png)

![](../images/line2.png)

##### `Step 4.`\|`ITB`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Connect the output of the **Sin** node to the top input of the **Mutliplication** node.

![connect sin to mult](images/sinToMult.png)

![](../images/line2.png)

##### `Step 5.`\|`ITB`| :small_orange_diamond:

*Pull* of the **Then 2** execution pin and place it into the **Branch** node you just to translate on x.

![connect execution pin to branch](images/connectThen2.png)

![](../images/line2.png)

##### `Step 6.`\|`ITB`| :small_orange_diamond: :small_blue_diamond:

Go into the game and turning each axis on and off. Also, look at your blueprint node chart as it runs to see how the booleans gate the operation flow.

https://user-images.githubusercontent.com/5504953/193456318-39ef7da9-817a-42c3-93c7-d537a18e1cf4.mp4

![](../images/line2.png)

##### `Step 7.`\|`ITB`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

Select the **File | Save All** then quit UE5.   Go to **P4V** and go the top project folder (the one that holds the `.uproject` file and **Content** folder) and press the <kbd>+Add</kbd> then <kbd>OK</kbd> button.  This makes sure any files that Unreal didn't add get added to source control. Press the <kbd>Submit</kbd> button and enter a message explaining the work done.  Press <kbd>Submit</kbd>.

![](../images/line.png)

<!-- <img src="https://via.placeholder.com/1000x100/45D7CA/000000/?text=Next Up - ADD NEXT TITBE"> -->
![next up next tile](images/banner.png)

![](../images/line.png)

| [previous](../translation/README.md#user-content-translation)| [home](../README.md#user-content-ue5-blueprints) | [next](../multiple-actors/README.md#user-content-dynamically-alter-multiple-classes)|
|---|---|---|
