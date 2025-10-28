# 🛠️ **Tutorial 5 - Cellpose: Segmenting Difficult Cells**

### **Background Scenario**

You're working with fluorescent microscopy images of touching cells. 
You’ve tried conventional thresholding and watershed segmentation in Fiji or ImageJ
— but the cells are touching, boundaries are unclear, and over- or under-segmentation is a 
common issue.

![ImageData](fluocells.png)

---

### **Goal:** 
Use **Cellpose** to generate accurate cell masks, separating individual cells, 
even in cluttered images. Then use **Fiji** to measurement cell properties.

---
### 5.1 Cellpose Segmentation

Start Cellpose by clicking on the Cellpose icon on your Desktop.

![ImageData](cellposeicon.png)

Your Cellpose GUI should look like this:

![ImageData](cellposegui.png)


---
#### ▶️ Step 1: Load Your Image



* Open your image using `File > Load image (*.tif, *.png, *.jgp)` in the GUI
* Your image should now appear in grayscale or RGB

---

#### ▶️ Step 2: Inspect the Cellpose GUI

You'll find different sections at the left hand side of the Cellpose GUI. 

* **Views** Control of channels, brightness and contrast
* **Drawing**: Selection how to show segmentation and control about manual annotations
* **Segmentation**: Parameters for Cellpose (cyto3) segmentation
* **Other models**: Selection of custom models or other Cellpose models (a.o. nuclei, cyto2)
* **Image restoration**: Performs denoising or filtering before segmentation if enabled
* **Scale disk on**: Size indicator as magenta disk at the lower left side of the image
* You can **Zoom** using the mouse wheel or <kbd>Ctrl</kbd> + <kbd>+</kbd> and <kbd>Ctrl</kbd> + <kbd>-</kbd> 

<br>

* Toggle the different views and adjust brightness and contrast for your channels.
* Which structures do channel 0 and channel 1 show?

--- 


#### ▶️ Step 3: Apply the pre-trained model (cyto3)

* Set the correct diameter of your cells - you can use a measurement from Fiji, estimate the size using the scale disk or click "Calibrate" to let Cellpose decide
* Select the channels you'd like to segment, "chan2" can be the nuclei channel to support segmentation
* **Flow threshold / cell probability:** Leave default for now
* **Use GPU:** Enable if you have one (optional but faster)

---

#### ▶️ Step 4: Run Segmentation

* Click **“Run cyto3"** or click run next the custom or data-specific models
* You’ll see overlaid segmentation mask
* Use **View** to change the display, e.g. show the segmentation outlines
* Evaluate: Are all cells segmented? Are there missed detections or merged objects?

<br>

* Compare results between the different **cyto** and **nuclei** models.
* Try adjusting the **diameter** or **flow threshold** — what changes?

---

#### ▶️ Step 5: Refine or Save

* Use the **brush tool** to manually correct any mistakes if needed
* Export masks as:

  * **Label Images**: `File > Save masks as PNG/tif`
  * **ROIs**: `File > Save outlines as .zip archive of ROI files for ImageJ`  

---

#### 🧪 **Challenge Exercise**

Try running Cellpose on:

* A brightfield image of adherent cells
* A DAPI-stained image with clustered nuclei
* A tissue section with mixed cell sizes

---

#### 📌 **Key Takeaways**

| Pros                       | Cons                                      |
| -------------------------- | ----------------------------------------- |
| Works “out of the box”     | Needs GPU for large images or 3D stacks   |
| Handles crowded cells well | Not ideal for thin, filamentous shapes    |
| Supports brightfield & RGB | May need tuning for unusual imaging types |
| No coding required         | Fine-tuning model requires annotation     |

---

#### 🔗 Useful Resources

* [Official Cellpose Tutorial (YouTube)](https://www.youtube.com/watch?v=K1o2YzEYrRc)
* [Cellpose GitHub Page](https://github.com/MouseLand/cellpose)


--- 

### 5.2 Import of Cellpose Results to Fiji

There are several ways to bring your **Cellpose** segmentation results into **Fiji** for further measurements and visualization.  
Choose the method that matches the type of output you exported.

---

#### ▶️ Option 1. Import ROIs (.zip) from Cellpose

If you exported **ROI files** directly from Cellpose:

1. Open your corresponding image in **Fiji**.  
2. Go to **`Analyze > Tools > ROI Manager`**.  
3. Click **`Open`** and select your exported **`.zip`** file.  
4. Your segmented objects will appear as ROIs — you can measure, label, or overlay them as needed.

> 💡 *Use* `Measure` *to get per-object area, mean intensity, or shape statistics.*

---

#### ▶ Option 2️. Import Label Images and Convert to ROIs

If you exported **label images** (where each object has a unique integer value):

1. Open the **label image** in Fiji.  
2. Run **`BIOP > Image Analysis > Label To ROI`**.  
3. A new ROI set is created in the **ROI Manager** to inspect or edit the results.  

If you want to exclude the cells at the image edges, use the **MorpholibJ** plugin:
**`Plugins > MorpholibJ > Label Images > Remove Border Labels`**

---

#### ▶ Option 3️. Run Cellpose Directly in Fiji

You can also run Cellpose inside Fiji via the **BIOP plugin**:

1. Go to **`BIOP > Cellpose/Omnipose > Cellpose`**.  
2. Set the parameters as previously defined in the Cellpose GUI. 
3. Click **`OK`**.  
4. The output will be a label image - you can transfer the label image to Fiji ROIs using the strategy above.

---

### 5.3 Object-based measurements

If you want to perform measurements inside individual cells/nuclei/compartments, you'll perform object-based measurements. 
In Fiji, there is no easy way to do this, but requires manual work.

1. Open the image you want to analyse
2. Import your cell segmentation to the Fiji ROI Manager (see 5.2)
3. Open your mitochondria segmentation or quickly threshold your mitochondria:
	* Median filter and Yen threshold, watershed
4. `Analyze > Set Measurements..`: Activate `Limit to threshold` and set `Redirect to:` to your original image
5. In your original image, select the channel you would like to measure
6. Now select the first ROI in the ROI Manager
7. Use `Analyze > Analyze Particles` and select `Summarize`. Then press `OK`. 
8. Repeat with the next ROI. 
8. Output: 
	* **Results table**: all individual measurements
	* **Summary table**: per cell measurement