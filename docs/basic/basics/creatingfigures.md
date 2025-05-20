### Creating Figures
!!! tip "Learning Objective"
    Learn how to create high-quality figures for publications using Fiji and OMERO.

* **RGB and Channels:**
    * `Image > Type > RGB Color` or `Image > Color > Split Channels`: Images can be opened as multi-channel (e.g., Red, Green, Blue). Use Split Channels to separate them for individual viewing and processing. Merge them back with `Image > Color > Merge Channels...`.  
    **Note:** If you convert an image to RGB Color, you lose access to the individual channels as separate data—they are merged into a single color image. The same applies if you split an RGB image: the original composite is lost, and you cannot easily recover the channel separation.
	
* **Overlay Handling and Flatten:**
    * `Image > Overlay > Add Overlay` / `Image > Overlay > Overlay Options...`: Overlays (such as ROIs, labels, or text) can be displayed above your image, remaining editable and non-destructive—they do not change the underlying pixel values.
    * `Image > Overlay > Flatten`: Flattens (merges) overlays into the image, making them permanent. This creates a new image where overlays become part of the pixels themselves and can no longer be removed or edited as overlays.
    * `Edit > Draw`: Another way to "burn in" overlays. With a selection active, use Draw to write it directly into the image data.

* **Scalebar:**
    * `Analyze > Tools > Scale Bar...`: Inserts a scale bar (e.g., 10 µm) onto the image. You can adjust the position, size, color, and label. For publications, always add a scale bar. If your image lacks scale information, set it first via `Image > Properties...`.

* **Timestamp:**
    * `Image > Stacks > Time Stamper...`: Adds a timestamp to each frame in a stack, indicating time or frame number. Useful for time-lapse sequences and videos. You can customize the format and position of the timestamp.

* **Sync Windows:**
    * `Plugins > Synchronize Windows`: Synchronize zooming and scrolling across multiple open images (e.g., different channels or samples). This is very helpful for comparative analysis.

* **Stack Tools:**
    * `Image > Stacks`: Provides many tools for handling image stacks (3D or time-lapse). Examples: create projections (`Image > Stacks > Z Project...`), extract sub-stacks (`Image > Stacks > Tools > Make Substack...`), split or merge stacks.

* **Image Properties:**
    * `Image > Properties...`: View and edit image metadata, such as pixel size, z-step (for 3D), units, number of channels/frames, and more. Essential for correct scaling and for ensuring accurate time or z-position in figures.
