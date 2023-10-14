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

In the editor change it to only **bTranslateOnY** as `true`. *Press* the <kbd>Play</kbd> button to see the box move in and out of the screen.

https://github.com/maubanel/UE5-Blueprints/assets/5504953/60ccf750-6c5f-4059-a507-57b74f0f3312

![](../images/line2.png)

##### `Step 4.`\|`ITB`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

*Copy and paste* the entire section from Y below it. Change the **Comment** to `Translate on Z`.  Right click on the **bTranslateOnY** node and select **Replace variable 'bTranslateOnY' with... | bTranslateOnZ`**.  This will change it to the **Z** axis.  Connect the **Lerp** from the Y section to **SetRelativeLocatoin | New Location Z**. Connect the **Alpha** of the **Lerp** to the **SIN** node.Connect the output of the **Sequence | Then 2** pin to the **Branch** node hooked up to **bTranslateOnZ**.

![copy and paste to translate on x](images/translateOnX.png)

![](../images/line2.png)

##### `Step 5.`\|`ITB`| :small_orange_diamond:

Press the <kbd>Play</kbd> button and now select **bTranslateOnZ**. I had to reduce the distance so that the cube doesn't go into the ground. Now try turning each axis on and hitting play. Notice that it is **NOT** movign on all three axis. We are only moving with the last Z axis.  Lets fix this.

https://github.com/maubanel/UE5-Blueprints/assets/5504953/74ba9cfa-94aa-4080-8956-d0be851cfb52

![](../images/line2.png)

##### `Step 6.`\|`ITB`| :small_orange_diamond: :small_blue_diamond:

We need to add the other axis back into the tranlation nodes.  We are zeroing them out.  Select the **TranslationCube** pin and select **GetRelativeLocation** and then **Split Struct Pin**.

![copy and paste to translate on x](images/getRelaticXLoc.png)

![](../images/line2.png)

##### `Step 7.`\|`ITB`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

Now connect the **Relative Location Y** to **Set Relative Location | New Location Y** and **Relative Location X** to **Set Relative Location | New Location Z**.  This will put the current value and not zero it out.

![alt_text](images/connectYZ.png)


![](../images/line2.png)

##### `Step 8.`\|`ITB`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Repeat it for the Y axis.  Right click on **TranslatingCube** and select a **Get Relative Location** node and **Split Struct Pin** from the output.  Now connect the **Relative Location X** to **Set Relative Location | New Location X** and **Relative Location Z** to **Set Relative Location | New Location Z**.  This will put the current value and not zero it out.

![alt_text](images/getRelativeYLoc.png)

![](../images/line2.png)

##### `Step 9.`\|`ITB`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Repeat it for the Z axis.  Right click on **TranslatingCube** and select a **Get Relative Location** node and **Split Struct Pin** from the output.  Now connect the **Relative Location X** to **Set Relative Location | New Location X** and **Relative Location Y** to **Set Relative Location | New Location Y**.  This will put the current value and not zero it out.

![alt_text](images/getRelativeZLoc.png)

![](../images/line2.png)

##### `Step 10.`\|`ITB`| :large_blue_diamond:

Select translation on all three axis and press the <kbd>Play</kbd> button. Now it is moving on all three axis, well done!

https://github.com/maubanel/UE5-Blueprints/assets/5504953/d2a8fd33-9839-4205-8cec-e447dedd321f

![](../images/line2.png)

##### `Step 11.`\|`ITB`| :large_blue_diamond: :small_blue_diamond: 

Select the **File | Save All** then press the <kbd>Revision Control</kbd> button and select **Submit Content**.  If you are prompted, select **Check Out** for all items that are not checked out of source control. Update the **Changelist Description** message and with the latest changes. Make sure all the files are correct and press the <kbd>Submit</kbd> button. A confirmation will pop up on the bottom right with a message about a changelist was submitted with a commit number. Quit Unreal and make sure your **Pending** tab in **P4V** is empty. **Submit** any work that is still in the editor.

![save all and submit to perforce in P4V](images/submitP4.png)

![](../images/line2.png)

##### `Step 12.`\|`ITB`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: 

Sometimes not all files get submitted to Unreal especially for files that don't show up in the editor.  It is good practice one you submit in **Unreal** and quit the game to right click on the top most project folder and select **Reconcile Offline Work...**.

This will either give a message saying ther is nothing to reconcile or bring up a tab.  Make sure that these are **NOT** files in the **Intermediate** and **Saved** folders as these should be ignored from the `.p4ignore`.

If the files are in **Content** or **Configuration** then press the <kbd>Reconcile</kbd> button.  Then submit the changes with a message and press the <kbd>Submit</kbd> button.

![reconcile offline work](images/reconcile.png) 

![](../images/line.png)

<!-- <img src="https://via.placeholder.com/1000x100/45D7CA/000000/?text=Next Up - ADD NEXT TITBE"> -->
![next up next tile](images/banner.png)

![](../images/line.png)

| [previous](../translation/README.md#user-content-translation)| [home](../README.md#user-content-ue5-blueprints) | [next](../multiple-actors/README.md#user-content-dynamically-alter-multiple-classes)|
|---|---|---|
