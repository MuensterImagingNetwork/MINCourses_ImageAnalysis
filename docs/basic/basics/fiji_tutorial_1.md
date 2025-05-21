## Tutorial 1: Open & inspect Images

!!! Warning "Note"
    Some images used in this tutorial are taken from the Bioimage Analysis book by Pete Bankhead ([bioimagebook.github.io](https://bioimagebook.github.io)). Content is licensed under [**CC-BY 4.0**](https://creativecommons.org/licenses/by/4.0/), except where noted otherwise. See License & Reuse for details.

---


###1. Start Fiji

!!! Tip "Exercise"
	Navigate to your Fiji folder (normally Fiji.app) and double click on `fiji-windows-x64`

!!! Warning "Fiji on the HIVE (MIN-Server)"
	You will find the course Fiji version on your Desktop. 
	You can find instruction on how to connect to the Hive in the confluence of the University Münster: [HIVE FAQ](https://confluence.uni-muenster.de/spaces/WWUIMW/pages/54528157/The+HIVE+-+FAQ) (Uni-MS internal)

![Fiji GUI](/assets/Fiji_GUI_notes.png)

- The **Menu Bar** at the top of the Fiji window provides access to all program functions, including opening and saving files, running plugins, analyzing images, and changing settings.

- The **Tool Bar** offers quick access to a range of drawing and Region of Interest (ROI) tools, such as rectangular, oval, polygon, and freehand selections, as well as the Wand Tool for automatic region selection. Additional toolsets for tasks such as development, working with stacks, and look-up tables (LUTs) can be selected from the tool bar's drop-down menu.

- The **Status Bar** (at the bottom of the window) displays important status messages and information, such as pixel coordinates, intensity values, and current activity in Fiji.

- The **Command Finder** is a powerful search feature that allows you to quickly locate and launch any Fiji command or plugin. Just start to type into the search field to find commands instantly. You can open the Command Finder by pressing `L` on your keyboard or by selecting `Plugins → Utilities → Command Finder` from the menu.
	
---
	
###2. Opening Images in Fiji

To open images in Fiji, you can simply drag and drop your image files directly into the Fiji window. In many cases, especially with proprietary microscopy formats, the *Bio-Formats Importer* window will automatically appear to guide you through the import process. 

Alternatively, you can open images using the menu: go to `File → Open...` and select your desired image file from your computer.

If you encounter problems opening your files and the *Bio-Formats Importer* window does not appear, you can start the import process manually. Go to `File → Import → Bio-Formats`, then browse and select your file. Bio-Formats supports a wide range of bioimaging file formats (such as `.lif`, `.czi`, `.nd2`, and more), ensures compatibility with many proprietary microscopy formats, and preserves important metadata during import.

!!! Tip "Exercise"
	**On Hive:** Navigate to `D:\PROJECTS\Courses\Image Analysis Courses\1_BasicsOfImageAnalysis\Fiji_Images` and open `hela-cells.tif` by drag and drop it to the Fiji GUI.  
	**Alternatively:** In Fiji go to `Plugins → Bio-Formats → Bio-Formats-Importer` and open
	`D:\PROJECTS\Courses\Image Analysis Courses\1_BasicsOfImageAnalysis\Fiji_Images\hela-cells.tif`
	


#### The Bio-Formats Importer Dialog
![Bio-Formats](/assets/bio-formats.png)

- By default, the following settings are usually enabled:
    - **Hyperstack**: Images are opened as hyperstacks, allowing you to easily navigate through different channels, z-slices, and time points.
    - **Color mode: Default**: The importer chooses the default color representation for the image.
    - **Autoscale**: Image intensities are automatically scaled for optimal display.
- Additional useful options include:
	- **Display ROI**: This option will display any Regions of Interest (ROIs) stored within the image metadata.
	- **Split Channels**: Allows you to separate the image into individual channel windows for more detailed analysis.
- You can adjust these and other options as needed to ensure your images are displayed according to your analysis requirements.

---

###3. Channel & Brightness and Contrast

!!! tip "Exercise"
    After you have opened `hela-cells.tif`, go to `Image → Adjust → Brightness/Contrast` or use the shortcut `Ctrl + Shift + C`.
    Drag the Channel Bar (indicated with a `C`) below the image and observe how the color of the Brightness and Contrast window changes. Additionally, notice that the headline (title) of the image updates according to the channel you select.

|     **Brightness and Contrast with Auto Adjustment**         |      **Brightness/Contrast**     |
|:----:|:----:|
| ![Hela-cells red](/assets/hela_red.png)      | ![Brightness/Contrast](/assets/bc_red.png)      |
| ![Hela-cells green](/assets/hela_green.png)  | ![Brightness/Contrast](/assets/bc_green.png)    |
| **Brightness and Contrast Adjusted** | **Min:270 Max: 1000**  |
| ![Hela-cells green](/assets/hela_green_adj.png) | ![Brightness/Contrast](/assets/bc_green_adj.png) |


!!! tip "Exercise"
    Now select a channel of your choice and adjust the histogram (brightness & contrast) using the minimum and maximum sliders.  
    Observe how changing the minimum or maximum value affects the image display.

??? tip "What is a Histogram?"
    A histogram shows the distribution of grayscale values (pixel intensities) in your image. The left side represents dark pixels, the right side bright pixels. The way intensities are displayed as colors depends on the chosen LUT (Lookup Table).

    When you set the minimum slider to a value (e.g., 100), all pixels with intensity 100 or lower will appear completely black. Similarly, if you move the maximum slider to a lower value (e.g., 200), all pixels with intensity 200 or higher will appear completely white. Intensities between the minimum and maximum are mapped linearly between black and white (or according to the LUT).

    Note: Adjusting the sliders only changes the display, not the actual pixel values. **Do not click "Apply"**—this will permanently change your image data and would affect any measurements, which is not recommended here.

---
	
###4. Open images from OMERO

The Münster Imaging Network (MIN) provides an [OMERO](https://www.openmicroscopy.org/omero/) server for managing and storing microscopy images. With the [OMERO Fiji plugin](https://www.openmicroscopy.org/omero/), you can connect directly to the OMERO server and load images into Fiji for analysis and processing. This allows you to access your microscopy data efficiently without the need to manually download files. If the plugin is not installed already to your Fiji, download the `omero_ij-xx.jar` file from the link above and copy it to the Fiji plugins folder. Detailed introductions can be found in the [OMER Guides](https://omero-guides.readthedocs.io/en/latest/fiji/docs/installation.html). 
OMERO Server at the MIN: [omero-imaging.uni-muenster.de](omero-imaging.uni-muenster.de)

!!! tip "Exercise"
	- Go to `Plugins → OMERO → Connect to OMERO` to open the **OMERO.insight** plugin.
	- Check if the server `omero-imaging.uni-muenster.de` is already configured
		- If not, click on the wrench and and in the next window on the plus to add the server `omero-imaging.uni-muenster.de`.
	- Type in in your ***University ID*** and ***University Password*** to log in.
	
	
|     **OMERO.insight Plugin**         |      **Setting Up the OMERO Server**     |
|:----:|:----:|
| ![OMERO Plugin](/assets/omero_insight_ij.png) | ![OMERO Server Settings](/assets/omero_server.png) |

!!! tip "Exercise"
	- Click on `Groups` and tick on the group: **MIN_Courses** and **All Members**
	- Now open on the left side the ***Project*** `Basics of Image Analysis` and the ***Dataset*** `ExampleImages`.
	- Doubleclick on a Thumbnail to open the image in Fiji.

![OMERO Fiji Plugin](/assets/omero_insight_groups.png)

![OMERO Fiji Plugin](/assets/omero_insight_images.png)

---

###5. Commonly Used Tools for Image Inspection

**Duplicate** (`Edit > Duplicate...`): Creates a copy of the current image or selection.  
**Shortcut:** `CTRl+Shift+D`

**Channels Tool** (`Image > Color > Channels Tool...`): Opens the channel management tool for viewing, splitting, or merging channels.  
**Shortcut:** `Shift+Z`

!!! tip "Exercise"
	- Open the `Channels Tool` and select `Color` or `Grayscale` or `Composite`.
	- Click through the different channels.


| ![Hela Cells Channel 2](/assets/hela_c2.png) | ![Channels Tool](/assets/channels_c2.png) | 
| :----: | :---------: | 
| ![Hela Cells Channel 2](/assets/hela_c2_gray.png) | ![Channels Tool](/assets/channels_c2_gray.png) |

**Lookup Tables** (`Image > Lookup Tables`): Apply different color maps (LUTs) to visualize grayscale images in color.  
You can also quickly select and switch LUTs using the LUT dropdown menu in the GUI Tool Bar or in the Channels Tool.

!!! tip "Exercise"
    - Select different LUTs and compare, for example, the "Blue" and "Gray" LUTs using the same Brightness & Contrast settings. What do you recognize?
    - Choose the "HiLo" LUT and adjust the histogram using the Brightness & Contrast tool:
        - <span style="color: blue;">**Blue**</span>: Pixels displayed with zero intensity (black).
        - <span style="color: red;">**Red**</span>: Pixels displayed with maximum intensity (white).
    - Click through the different channels to see how the LUT and histogram settings affect each one.
	
|     **Channel 2 with gray LUT, full range**         |      **Channel 2 with blue LUT, full range**     |
| :----: | :---------: |
| ![Hela Cells Channel 2](/assets/hela_c2_gray2.png) | ![Channels Tool](/assets/hela_c2_blue.png) |




|     **Channel 2 with the LUT HiLo**         |
| :----: | 
| ![Hela Cells Channel 2](/assets/hela_c2_hilo.png) | 



**Split Channels** (`Image > Color > Split Channels`): Separates a multi-channel image into individual grayscale channel images.

**Merge Channels** (`Image > Color > Merge Channels`): Combines separate channel images into a single multi-channel or RGB image.

**Z Project** (`Image > Stacks > Z Project...`): Processes a z-stack to create a 2D projection image from multiple z-slices.  
Alternatively, you can access this function from the toolbar menu under "stk".

!!! tip "Exercise"
    - Open the 5D Fiji sample image: `File > Open Samples > Mitosis`.
    - Navigate through the Z-stack and time points using the sliders below the image.
    - Duplicate the image with `Ctrl+Shift+D`.
    - Go to `Image > Stacks > Z Project...`, and select **Max Intensity** as the projection type.
    - Step through the different time points in the resulting projection.

    *Tip: Using Duplicate, you can also create and work with substacks.*
	

| **Mitosis, t:29, z:5**             | **Mitosis, t:29, MIP**          |
| :---------------------------------:| :------------------------------------------------------:|
| ![Mitosis](/assets/mitosis.png)    | ![Mitosis](/assets/mitosis_mip.png)                     |