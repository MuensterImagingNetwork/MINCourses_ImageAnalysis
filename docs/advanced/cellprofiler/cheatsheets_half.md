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