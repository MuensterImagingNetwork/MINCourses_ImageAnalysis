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

These tools, when combined thoughtfully, allow you to build powerful workflows to solve many common image analysis challenges. The following practical exercises will guide you through applying these steps.

!!! note "Ready to Practice?"
    The best way to understand these concepts is to apply them. Let's dive into the practical exercises with the trainer!
