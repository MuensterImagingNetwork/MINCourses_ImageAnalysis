# 🧪 **Hands-on ilastik: Segmenting Nuclei with Pixel Classification**

### Background Scenario

You’ve acquired 3D fluorescence microscopy images with two channels:

* **Green:** cytoplasmic marker
* **Blue:** nuclear stain (e.g., DAPI)

**Goal:** Segment individual nuclei from the blue channel, even in crowded or noisy areas.

---

### ⚠️ Where Traditional Segmentation Fails

You try global thresholding using **Otsu’s method** on the nuclear channel:

* 🔍 **Problem:**

  * Merged adjacent nuclei
  * Faint nuclei missed entirely
  * Intensity variation and texture not handled

📸 **Result Example:**
Left: thresholded image with merged objects
Right: ground truth outlines showing individual nuclei

🧪 **Take‑home message:**
We need a smarter method that considers *context* and *local features*—not just intensity.
Let’s use a **pixel classifier** in ilastik!

---

## 🧭 **Step-by-Step Instructions**

---

#### 📁 Step 1: Start a New Project

* Open **ilastik**
* Select the **Pixel Classification** workflow
* Create a new project and name it meaningfully (e.g., `nuclei_segmentation.ilp`)

---

#### 🖼️ Step 2: Import Your Image

* Go to **Input Data > Add New**
* Load your image (TIFF or HDF5 preferred)
* Preview it in the image viewer to ensure it loads correctly

---

#### 🧪 Step 3: Select Features

* Navigate to the **Feature Selection** tab
* ilastik will compute image features like:

  * Intensity
  * Edges
  * Texture
* Choose multiple feature scales (σ values).
  Example: `0.3`, `1.0`, `3.5`, `5.0`
* These help the classifier distinguish fine vs. coarse structures.

---

#### 🏷️ Step 4: Define Classes

* Add two classes:

  * **Class 1**: *Nucleus*
  * **Class 2**: *Background*
* You can rename classes by double-clicking their labels

---

#### ✍️ Step 5: Annotate Training Regions

* Use the **paintbrush** tool to label regions for each class
* Cover a variety of image areas:

  * Bright nuclei
  * Dim nuclei
  * Crowded regions
  * Background noise
* Label at least 5–10 representative regions per class

---

#### 🔄 Step 6: Train the Classifier

* Activate **Live Update** (top left of viewer)
* ilastik will update a **probability map** in real time
* Bright areas = high likelihood of being “nucleus”

---

#### 🧹 Step 7: Refine Annotations

* If the classifier is making mistakes:

  * Add or erase brush strokes
  * Focus on misclassified edge areas or noisy zones
* Live Update helps you immediately see the effect of changes

---

#### 💾 Step 8: Export the Probability Map

* Go to the **Prediction Export** tab
* Choose what to export:

  * Raw probability map (for post-processing in Fiji/ImageJ)
  * Binary segmentation mask
* You can also export as TIFF or HDF5

---

#### 🔁 Step 9: Batch Apply to New Images

* In **Batch Input**, load additional images
* ilastik will apply your trained classifier across the entire set
* Great for high-throughput image analysis

---

Let me know if you'd like a companion **Fiji post-processing tutorial** (e.g., for thresholding and watershed) or to expand this for **3D segmentation**!

---

### 🧪 **Challenge Exercise**

* Try training on a noisy image vs. a clean one. How does performance change?
* Train with **3 classes**: background, nucleus, and cytoplasm—see how the segmentation behaves.

---

### 📌 **Key Takeaways**

| ✅ **Pros**                                  | ⚠️ **Cons**                                               |
| ------------------------------------------- | --------------------------------------------------------- |
| No coding or deep learning knowledge needed | Initial manual labeling takes time                        |
| Learns from pixel patterns & textures       | Classifier might need tuning per dataset                  |
| Great for complex or noisy images           | Segmentation is 2D (for now) unless using other workflows |
| Fast batch processing after training        | Watershed post-processing sometimes required              |

---

### 🔗 **Resources & Downloads**

For a detailed recap of the demonstration of the Pixel Classification Workflow in ilastik, 
please visit the [Ilastik page](https://www.ilastik.org/documentation/pixelclassification/pixelclassification).


* [ilastik Homepage](https://www.ilastik.org/)
* [Video Tutorials](https://www.youtube.com/@ilastik)
* [Documentation](https://www.ilastik.org/documentation/pixelclassification/pixelclassification)
---


!!! warning "Citation"
	When using Ilastik for your image analysis, please cite:
	>***ilastik: interactive machine learning for (bio)image analysis*** <br>
	Stuart Berg, Dominik Kutra, Thorben Kroeger, Christoph N. Straehle, Bernhard X. Kausler, Carsten Haubold, 
	Martin Schiegg, Janez Ales, Thorsten Beier, Markus Rudy, Kemal Eren, Jaime I Cervantes, Buote Xu, Fynn Beuttenmueller, Adrian Wolny, Chong Zhang, Ullrich Koethe, Fred A. Hamprecht & Anna Kreshuk
	in: Nature Methods, (2019) 
	<br> DOI: [10.1038/s41592-019-0582-9](10.1038/s41592-019-0582-9)
