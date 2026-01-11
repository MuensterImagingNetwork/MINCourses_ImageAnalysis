# Cell Tracking

Cell tracking aims to follow objects (cells, nuclei, particles) over time in time-lapse image data. Automated tracking enables quantitative analysis of dynamic biological processes that would be impractical to perform manually.

---

## Advantages of Automated Tracking

- Handles large datasets consistently and reproducibly  
- Enables quantitative measurements over time (speed, displacement, lineage, intensity changes)  
- Reduces user bias compared to manual tracking  
- Makes complex behaviors (division, migration, merging) analyzable at scale  

---

## How Does Automated Tracking Work?

Automated tracking typically follows one of two strategies:

- **Segmentation + matching**  
  Objects are segmented in each frame, then corresponding objects are matched between consecutive time points.

- **Spot detection + linking**  
  Objects are detected as spots (e.g. intensity peaks), which are then linked across frames.

Both approaches rely on spatial proximity, object features, and movement constraints.

[Tracking cells in microscopy image data](https://f1000research.com/slides/11-744))

---

## General Steps in a Tracking Workflow

1. **Spot Detection or Segmentation**  
   Identify objects independently in each time frame.

2. **Tracking Algorithm**  
   Link objects over time based on distance, motion models, and optional feature similarity.

3. **Maximum Distance**  
   Define how far an object is allowed to move between consecutive frames.

4. **Gap Closing**  
	Allow tracks to bridge missing detections  
	- Maximum gap size (time)  
	- Maximum gap distance

5. **Divisions / Merges**  
   Optionally allow track splitting (cell division) or merging events.

6. **Inspect Tracks & Filter**  
   Remove implausible spots or tracks based on length, speed, or behavior.

7. **Measurements Over Time**  
   Extract time-resolved features (e.g. velocity, directionality, intensity, lineage).

---

## Tips & Tricks

- **Good detection or segmentation is key** — tracking cannot fix poor input.
- Choose the **correct spatial and temporal sampling resolution**.
- **Rule of thumb:** object movement between frames should be ≤ 20% of the typical distance to neighboring objects.
- For **rhythmical processes** (e.g. heart beats), acquire images at least **4× faster** than the biological frequency.
- **Only use what you need:**
	  - Reduce search radius to avoid unrealistic jumps.
	  - Use feature weighting only if object shape/intensity is stable over time.
	  - Do not allow fusions or divisions unless biologically required.
- Tracking is difficult — **take your time**.
- Iterate: adjust parameters, rerun tracking, inspect results.
- Try **advanced detectors** if simple methods fail.
- Visualize track statistics (length, speed, number of splits) to identify implausible regions.
- Apply **spot and track filters** before extracting quantitative features.
- Save your tracking configuration (e.g. as an `.xml` file) for reproducibility.
- Repeat the tracking after a week on the same data:  
  *What changed? Why?* — this helps reveal subjective choices and hidden assumptions.

(partially derived from: EMBO course on 3D Developmental Imaging, Oeiras, July 2022, Robert Haase)



---
