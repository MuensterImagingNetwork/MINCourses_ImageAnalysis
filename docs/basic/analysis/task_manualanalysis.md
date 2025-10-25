## 🔬 **Final Challenge: Quantify Mitochondrial Size in Fiji!**

### 🏁 **Your Mission**

You’ve practiced each step of image preprocessing, segmentation, and measurement — now it’s time to combine them into a complete workflow!  

**Perform a full image analysis to measure mitochondrial size in BPAE cells.**  
You’ll filter the image, segment mitochondria, analyse them quantitatively, and inspect your results for accuracy.

---

### 💡 **Pro Tips**

| ✔ Do This                                      | ✘ Avoid This                           |
| ---------------------------------------------- | -------------------------------------- |
| Test different filters and compare results     | Applying filters blindly               |
| Inspect your binary mask before measuring      | Measuring unverified segmentations     |
| Use *Redirect to original image* for intensity | Measuring on the binary mask only      |
| Use “Exclude on Edges” in Analyze Particles    | Counting cropped mitochondria          |

---

### 🧭 **Your Tasks**

#### ▶️ Step 1: Preprocess and Filter Your Image  
* Open the **mitochondria channel** of your BPAE image.  
* Test one or more filters to clean up noise:  
	  - `Process > Subtract Background...`  
	  - `Process > Filters > Gaussian Blur...`  
	  - `Process > Filters > Median...`  
	  - *(Optional)* Try `Difference of Gaussians (DoG)` to enhance small structures.  
* Compare different filter combinations and note which gives the clearest mitochondrial structures.

> 💡 *Think:* How does filter size affect the visibility and separation of mitochondria?

---

#### ▶️ Step 2: Threshold and Segment  
* Go to `Image > Adjust > Threshold...`  
* Experiment with different methods (Otsu, Yen, Li, etc.).  
* Apply the threshold to create a **binary mask** showing mitochondria as white objects.  

> 💡 *Tip:* Duplicating your image before thresholding helps you easily compare results.

---

#### ▶️ Step 3: Set Measurements  
* Go to `Analyze > Set Measurements...`  
* Select:  
	  - *Area*  
	  - *Mean intensity*  
	  - *Shape descriptors* (optional)  
* If your binary image was derived from a filtered version, use **Redirect to:** your **original mitochondrial image**.

---

#### ▶️ Step 4: Analyze Particles & Inspect ROIs  
* Run `Analyze > Analyze Particles...`  
	  - Set a reasonable **size range** (e.g., 0.1–10 µm²).  
	  - Check **Display Results** and **Add to Manager**.  
	  - Enable **Exclude on Edges** to ignore cropped mitochondria.  
* Inspect your ROIs in the **ROI Manager** and confirm that they match visible mitochondria.

---

#### ▶️ Step 5: Review and Summarize Your Results  
* Check the **Results Table** for the area measurements of mitochondria.  
* Calculate the **average mitochondrial size** (e.g., in Excel or using Fiji’s `Results > Summarize`).  
* Optionally, create a histogram of mitochondrial area distribution (`Analyze > Distribution...`).

> 🎯 *Goal:* Obtain a reliable estimate of the average mitochondrial size and evaluate whether your segmentation matches the visible structures.

---



