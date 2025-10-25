## 🤖 **Final Challenge: Segment and Quantify Cells with Cellpose and Fiji!**

### 🏁 **Your Mission**

Deep learning can make segmentation fast and accurate — especially for complex shapes like cells!  
In this challenge, you’ll use **Cellpose** to segment whole cells based on **actin and nuclei** signals,  
then measure cell size in **Fiji**.  

As an optional advanced step, you’ll combine your **cell segmentation** with a **mitochondria mask**  
to measure mitochondrial size *per individual cell*.

---

### 💡 **Pro Tips**

| ✔ Do This                                        | ✘ Avoid This                            |
| ------------------------------------------------ | --------------------------------------- |
| Use both actin and nuclei channels for Cellpose  | Running on a single, low-contrast channel |
| Check segmentation quality before exporting       | Measuring on poor or incomplete masks    |
| Use *Redirect to original image* for intensity    | Measuring on binary masks only           |
| Keep units consistent (µm²)                      | Mixing pixels and micrometers            |

---

### 🧭 **Your Tasks**

#### ▶️ Step 1: Prepare Your Image  
* Open your **multi-channel image** (actin + nuclei + mitochondria) in Fiji.  
* Identify which channels represent:  
	  - **Actin** (cell outline)  
	  - **Nuclei** (cell center)  
	  - **Mitochondria** (for later use)  
* Save the image (e.g., as `.tif`) and make note of the actin and nuclei channel numbers.

---

#### ▶️ Step 2: Segment Cells in Cellpose  
1. Open **Cellpose** and load your multi-channel image.  
2. Choose the **cyto2** model (optimized for full-cell segmentation).  
3. Assign the input channels:  
	   - **Channel 1 (cytoplasm):** *Actin channel*  
	   - **Channel 2 (nuclei):** *Nuclear channel*  
4. Adjust parameters if needed:  
	   - Diameter
	   - Flow threshold and cell probability
5. Run segmentation and **visually inspect** the results.  
	   - Are cell boundaries complete and accurate?  
	   - Are touching cells properly separated?

> 💡 *Tip:* Use zoom and outline display mode to check for over- or under-segmentation.

---

#### ▶️ Step 3: Export Segmentation Results  
* Export the **label image (mask)** as `.tif`.  
* Also export **ROIs** for Fiji.  
* Save both files to your working folder for Fiji analysis.

---

#### ▶️ Step 4: Measure Cell Size in Fiji  
* Open your exported **Cellpose label image** or **ROIs** in **Fiji**.  
* Open the original actin image alongside it for reference.  
* Go to `Analyze > Set Measurements...` and select:  
	  - *Area*  
	  - *Shape descriptors*  
	  - *(Optional)* *Mean intensity*  
* If measuring intensity, use **Redirect to:** the **original actin image**.  
* Run `Analyze > Measure` or `Analyze > Analyze Particles...`  
	  - Include *Add to Manager*  
	  - Enable *Exclude on Edges*  

> 🎯 *Goal:* Calculate the **average cell area** from your dataset.

---

#### ▶️ Step 5 (Optional Advanced Challenge):  
### Measure Mitochondrial Size per Individual Cell  

1. Import your **mitochondria segmentation mask** into Fiji.  
2. Load your **cell ROIs** from the Cellpose segmentation.  
3. For each cell ROI:  
	   - Select it in the ROI Manager  
	   - Use `Image > Duplicate...` (*Duplicate only selected region*)  
	   - Measure mitochondria within that ROI using `Analyze Particles...`  
4. Calculate for each cell:  
	   - **Mitochondria count**  
	   - **Average mitochondrial size**

> 💡 *Bonus:* Compare mitochondrial size per cell — do larger cells have larger or more mitochondria?

---

