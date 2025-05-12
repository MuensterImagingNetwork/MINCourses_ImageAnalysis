# Hands-On - CellProfiler Tutorial

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

You can find the detailed tutorial in your course folder. 
