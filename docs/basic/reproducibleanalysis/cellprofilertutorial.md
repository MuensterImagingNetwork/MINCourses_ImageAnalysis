# 🛠 **Hands-On CellProfiler: Creating a reproducible analysis pipeline**

### **Background Scenario**
![ImageData](vargas_image.jpg)
**© Copyright by Pascual-Vargas et al.** |
[Source](https://idr.openmicroscopy.org/webclient/img_detail/2874783/?well=1246992)

The data we will analysis today, is derived from this research paper: 

>***Analysis of YAP/TAZ localization in triple negative breast cancer in response to Rho GTPase regulators*** <br>
Pascual-Vargas P, Cooper S, Sero J, Bousgouni V, Arias-Garcia M, Bakal C., Scientific Data, 2017

[Publication](https://pmc.ncbi.nlm.nih.gov/articles/PMC5332010/) | [Full Dataset](https://idr.openmicroscopy.org/webclient/?show=screen-1651)


### Research question for today:

**What is the YAP/TAZ ratio between nucleus and cytoplasm?**

Create an image analysis pipeline using CellProfiler to calculate the 
YAP/TAZ ratio between nucleus and the cytoplasm in this dataset.


**Analysis strategy:**

- (Image preprocessing)
- Segment nuclei and cytoplasm
- Assign each cytoplasm one nucleus
- Measure intensity parameters for nucleus and cytoplasm
- Calculate Yap/Taz Ratio
- Export the results


---

### 🧭 Step‑by‑Step Instructions

You can launch CellProfiler on JupyterHub via the **CellProfiler** icon, or on the HIVE using the Anaconda Prompt and type:

```bash
conda activate cellprofiler-cellpose
cellprofiler
```

---

#### 📂 Step 1: Load Your Images

* Right click on the "Drop field" --> "Browse for Folder"
* Select your dataset directory (> 1_BasicsOfImageAnalysis > 3_Hands-On_Cellprofiler > Data)


---

#### 🔖 Step 2: Metadata

* In **Metadata**, extract image identifiers.
	- choose "Extract metadata?": Yes
	- select "Metadata extraction method": Extract from image file headers
	- click on "Extract metadata"
	- at the table below, click "Update"
	

---


#### 🧹 Step 3: NamesAndTypes

* In **NamesAndTypes**, assign channels:
	- "Assign a name to" : "Images matching rules"
	- Assign "Nuclei" to images containing "C1" in their file names. 
	Select "Add another image" and assign "Actin" to files containing ""C2". 
	Continue with “Tubulin” for “C3” and “YapTaz” for “C4”. 
		* **C1**: Nuclei
		* **C2**: Actin
		* **C3**: Tubulin
		* **C4**: YapTaz
		* **Channel 2:** YAP/TAZ → signal of interest
	- Click on the Update button to display a table that shows each channel pair matched up for the wells in the assay.

---
- Start **Test Mode**
---

#### ⚪ Step 4: Identify Nuclei

* Add a ***RunCellpose"** module

  * Select the appropriate detection mode for nuclei
  * Select your input image ("Nuclei")
  * Typical diameter: 10-30 pixels
  * Give a meaningful name to your output object (e.g. "Nuclei_Segmentation")
  * Review segmentation overlay and adjust diameter or threshold settings until nuclei are well separated.

---

#### 🌐 Step 5: Identify Cell Bodies (Cytoplasm)

* Add a ***RunCellpose"** module

  * Select the appropriate detection mode for cytoplasm
  * Select your input image ("Actin")
  * Typical diameter: 50-80 pixels
  * Give a meaningful name to your output object (e.g. "Cytoplasm_Segmentation")
  * Review segmentation overlay and adjust diameter or threshold settings until nuclei are well separated.

---

#### 🔗 Step 6: Relate Objects

* Add **“RelateObjects”** to verify each cytoplasm is assigned to its nucleus.
* Choose "Cytoplasm_Segmentation" as Parent Object and "Nuclei_Segmentation" as Child Objects
* Save the children with parents as new object set with a meaningful name (e.g. "Nuclei_Seg_Relate")

---

#### 📊 Step 7: Measure Intensities

* Add **“MeasureObjectIntensity”**

  * Measure YAP/TAZ channel intensities in both nuclei and cytoplasm objects.
  * You need to select the images that you'd like to measure ("YapTaz")
  * You also need to select the objects that you'd like to measure ("Nuclei_Seg_Relate")

---

#### ➗ Step 8: Compute YAP/TAZ Ratio

* Add **“CalculateMath”**

  * Formula: `IntegratedIntensity_Nucleus / IntegratedIntensity_Cytoplasm`
  * Name the output measurement **`YAP_TAZ_ratio`**

!!! tip
	If you get stuck here, you might want to check out the example project "ImageAnalysis_ExampleProject_RatioMeasurement.cpproj" ;-)
  
---

#### 💾 Step 9: Export Results

* Add **“ExportToSpreadsheet”**

  * Select measurements: `YAP_TAZ_ratio`, object IDs, metadata
  * Choose CSV output path (e.g., `results/YAP_TAZ_ratios.csv`)
  
* Save your pipeline via **File > Save Project As** (e.g., `YAP_TAZ_pipeline.cpproj`).


---

#### 🔄 Step 10: Analyse your images in Batch‑process

* Once your pipeline is finished, you can hit "Analyze Images" and start analysis!

---

#### Exercises:

🧰 **Task:** <br>
Inspect the results output for both images and results table

🧰 **Task:** <br>
Add another measurement module from the “Measurement” module category and configure it. 
Which modules make sense, which don’t? <br>
You can find more info on the measurements here: https://cellprofiler-manual.s3.amazonaws.com/CellProfiler-4.2.6/modules/measurement.html

🧰 **Task:** <br>
Open the *ImageAnalysis_ExampleProject_RatioMeasurement.cpproj"*.
What is the purpose the **GrayToColor**, **OverlayOutlines**, **DisplayDataOnImage**, and **SaveImages** modules?
Why is it a good idea to add them to your pipeline?


### 📌 Key Takeaways

| ✅ Pros                                         | ⚠️ Cons                                                           |
| ---------------------------------------------- | ----------------------------------------------------------------- |
| GUI‑driven, no coding required                 | Initial setup of modules can be time‑intensive                    |
| Fully modular: you see every processing step   | Large pipelines may feel overwhelming at first                    |
| Transparent settings: all parameters are saved | Complex scripts require Python integration                        |
| Batch‑process dozens of images with one click  | Advanced analyses (e.g., machine learning) need plugins or export |

---

### 🔗 Useful Resources

* **CellProfiler Documentation:** [https://cellprofiler.org/docs](https://cellprofiler.org/docs)
* **Example Pipelines Gallery:** [https://cellprofiler.org/examples](https://cellprofiler.org/examples)
* **Video Tutorials:** [https://www.youtube.com/c/CellProfiler](https://www.youtube.com/c/CellProfiler)
* **Discussion Forum:** [https://forum.image.sc](https://forum.image.sc)