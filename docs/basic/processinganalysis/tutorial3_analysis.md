## Tutorial: Thresholding Images

###1. Start Fiji

!!! tip "Exercise"
    - Open the 5D Fiji sample image: `File > Open Samples > Mitosis`.
    - Navigate through the Z-stack and time points using the sliders below the image.
    - Duplicate the image with `Ctrl+Shift+D`.
    - Go to `Image > Stacks > Z Project...`, and select **Max Intensity** as the projection type.
    - Step through the different time points in the resulting projection.

<img src="/../../assets/t3_thresholding.png" alt="Thresholding" width="800">
*Image segmentation to obtain information about the intranuclear structures such as size and change, structure count as well as the intensity of cells and nuclei.* <br>






* **Subtract Background / Denoise:**
    * `Process > Subtract Background...`: Corrects for uneven illumination.
    * `Process > Noise > Denoise...` or `Process > Filters > Gaussian Blur...`: Reduces random noise, making subsequent steps more reliable.
* **Median Filter:**
    * `Process > Filters > Median...`: Effective for removing salt-and-pepper noise while preserving edges better than a simple blur.
* **Thresholding:**
    * `Image > Adjust > Threshold...` (e.g., using Otsu's method): Converts a grayscale image into a binary image (black and white) by separating pixels into foreground (objects) and background based on their intensity.
* **Binary Operations:**
    * `Process > Binary > Options...` (then `Close-`, `Open-`, `Fill Holes`, `Erode`, `Dilate`): Refine binary images. For example, `Close-` (dilate then erode) can fill small holes within objects and smooth their outlines.
* **Watershed Segmentation:**
    * `Process > Binary > Watershed`: Separates touching objects in a binary image, often used after thresholding when objects are clumped together.
* **Analyze Particles:**
    * `Analyze > Analyze Particles...`: Measures properties (area, shape descriptors, etc.) of objects in a thresholded binary image and can generate ROIs for each identified particle.
