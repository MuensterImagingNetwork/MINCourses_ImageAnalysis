# 🛠 Module Cheat Sheet

### 🖼️ **Images**

**Purpose:** Load your image files into CellProfiler.

**Essential Actions:**

* Click *Add Images* to browse and load files.
* Confirm that images appear in the table.

**Key Settings:**

* File filter (if needed): e.g. `*.tif`
* Folder location

---

### 🏷️ **Metadata**

**Purpose:** Extract information (e.g. channel, timepoint) from the metadata.

**Essential Actions:**

* Enable if filenames contain useful info (e.g. "WellA1\_T1").

**Key Settings:**

* Use *Extract from image file headers*
* Click on "Extract metadata"
* At the table below, click "Update"

---

### 🧩 **NamesAndTypes**

**Purpose:** Tell CellProfiler which image is which (e.g. channels, masks, segmentations).

**Essential Actions:**

* Define name for each image type (e.g. “Nuclei”)
* Assign color format (e.g. grayscale or RGB)

**Key Settings:**

* Rule-based file matching (e.g. filename contains “DAPI” → Name as “Nuclei”)
* Select image type: Grayscale / Color

---

### 🧠 **RunCellPose**

**Purpose:** Use deep learning (CellPose) to detect objects like nuclei or cells.

**Essential Actions:**

* Select the image to segment (e.g. “Nuclei”)
* Choose a model (e.g. *cyto*, *nuclei*)

**Key Settings:**

* Input image: e.g. “Nuclei”
* Output name: e.g. “Cells”
* Model: `cyto`, `nuclei`, or custom

---

### 🔍 **IdentifyTertiaryObjects**

**Purpose:** Define the area around a nucleus that belongs to the cytoplasm.

**Essential Actions:**

* Combine two objects: e.g. “Cells” and “Nuclei” to get “Cytoplasm”

**Key Settings:**

* Larger object: “Cells”
* Smaller object: “Nuclei”
* Output: “Cytoplasm”

---

### 📐 **MeasureObjectSizeShape**

**Purpose:** Measure shape features (area, perimeter) of segmented objects.

**Essential Actions:**

* Choose which object(s) to measure (e.g. “Nuclei”)

**Key Settings:**

* Objects to measure: “Nuclei”, “Cells”, etc.

---

### 💡 **MeasureObjectIntensity**

**Purpose:** Measure how bright objects are in each image.

**Essential Actions:**

* Choose the image and the object

**Key Settings:**

* Image: e.g. “GFP”
* Object: e.g. “Nuclei”

---

### 🧾 **ExportToSpreadsheet**

**Purpose:** Save measured results as a spreadsheet (.csv file).

**Essential Actions:**

* Choose which measurements to export

**Key Settings:**

* Output location (default is fine)
* Select “All measurements” or specify

---

### 🧃 **OverlayOutlines**

**Purpose:** Visualize segmented objects over original images.

**Essential Actions:**

* Choose an image and object outlines

**Key Settings:**

* Image: e.g. “Original”
* Outlines: e.g. “Nuclei”
* Output: e.g. “Nuclei\_Overlay”

---

### 💾 **SaveImages**

**Purpose:** Save any image generated during analysis (e.g. overlays).

**Essential Actions:**

* Select which image to save

**Key Settings:**

* Image: e.g. “Nuclei\_Overlay”
* Format: PNG or TIFF
* Output folder: e.g. “output/overlays”

---

Would you like a visual version of these recipe cards (e.g. printable handouts or slides with icons and example screenshots)? I can generate those too.
