<img src="/assets/fiji_logo.png" alt="Fiji Logo" width="150">
## Fiji

### **What is Fiji?**  
Fiji stands for “**Fiji Is Just ImageJ**”. Fiji is an open-source image processing package based on [ImageJ](https://imagej.net/). It is designed for scientific multidimensional image analysis and comes with a curated set of powerful plugins. 

---

### What is Fiji used for?
Fiji is widely used for biological image analysis, including tasks such as image segmentation, registration, tracking, and visualization of data from a variety of microscopy techniques.

---

### Download Fiji
- Official Fiji Website: https://fiji.sc/  
- Fiji-MIN Package: The Fiji-MIN package consist of the practical MIN-Toolbar and some already installed Plugins. [Download Fiji with the MIN-Toolbar](https://uni-muenster.sciebo.de/s/7LJ7fBS6PKi6nGi)  
<img src="/assets/MIN_Toolbar.png" alt="MIN_Toolbar" width="150">

---

### Citation of Fiji 

!!! warning "Citation"
	If you use Fiji in your research, please cite:  
	***Fiji: an open-source platform for biological-image analysis.*** <br>
	Schindelin, J., Arganda-Carreras, I., Frise, E., Kaynig, V., Longair, M., Pietzsch, T., 
	et al. (2012). *Nature Methods*, 9(7), 676–682. <br>
	DOI: [doi:10.1038/nmeth.2019](https://doi.org/10.1038/nmeth.2019)

---

### Strength through plugins
**TrackMate, Coloc2, Weka, Bio-Formats, StarDist, and more** <br>
Fiji’s power lies in its diverse ecosystem of plugins. Notable examples include:

- [TrackMate](https://imagej.net/plugins/trackmate) for cell tracking, single-particle tracking, and lineage analysis  
- [Coloc2](https://imagej.net/plugins/coloc-2) for colocalization analysis  
- [Trainable Weka Segmentation](https://imagej.net/plugins/tws/) for machine learning-based image segmentation  
- [Bio-Formats](https://imagej.net/formats/bio-formats) for reading and writing more than 150 proprietary microscopy file formats  
- [StarDist](https://imagej.net/plugins/stardist) as a state-of-the-art deep learning tool for object detection and segmentation in microscopy images  

This extensibility makes Fiji highly adaptable to new scientific developments and specific research needs.

---

### Install Plugins / Update Sites

**Installing and Managing Plugins**

* **Automatic Installation and Updates via the Fiji Updater:**
    * Go to `Help > Update...`
    * Fiji will check for available updates to the core application and all installed plugins.
    * To access more plugins, click "Manage update sites" in the updater window and enable the desired sites (e.g. "BioVoxxel", "OME", "CLIJ2", etc.). Update sites are community-maintained repositories with specialized tools.
    * After enabling sites, click "Close" and then "Apply changes" to install updates and new plugins.
    * Restart Fiji after updating.

* **Manual Plugin Installation:**
    * Download the plugin file (usually a `.jar`) from the developer's website.
    * Place the file in the `plugins` folder inside your Fiji installation directory.
    * Restart Fiji to load the new plugin.

* **Tip:** Regularly run the updater via `Help > Update...` to keep Fiji and your plugins current. This reduces compatibility issues and ensures access to the latest tools.

**Using Multiple Fiji Versions**

It is possible—and often helpful—to use multiple Fiji installations in parallel by copying and renaming the Fiji installation folder. This is useful for important analyses or reproducibility, as some plugins or update site combinations can conflict or behave differently with updates. Keeping a backup of a "known good" Fiji version can help avoid interruptions in workflows if newly installed plugins cause issues.

---

_Note: Some plugins require additional dependencies. The updater usually installs these automatically when you have the relevant update sites enabled._