---
From: youtube
created: 2025-08-10
tags:
  - fleeting
  - inbox
source: https://www.youtube.com/watch?v=yaa13eehgzo
---
---

## **1. Main Points Dealt With in the Video**

1. **Animation Workflow**
    
    - No single “ultimate” software; each tool has strengths and limitations.
    - Workflow is a combination of different programs depending on the task.
    
2. **Core Tools**
    
    - **Adobe After Effects** — Main animation/compositing tool for arranging scenes, adding text, effects, and synchronizing to audio.
    
    - **Python** — For programmatically generating animations, especially complex or math-heavy visualizations.
	    
        - **Manim** — Graph theory & certain math animations.
        
		- **Matplotlib** — Data plots, wave animations, complex system visualization.
    
    - **Blender** — 3D animation, neuron models, surfaces, slicing effects.
    
3. **Supporting Tools (Adobe Suite)**
    
    - Illustrator — Vector graphics, diagrams.
    - Photoshop — Thumbnails, raster editing.
    - Premiere Pro — Video editing, cutting, arranging.
    - Audition — Audio cleanup & enhancement.
	
4. **Example Animation Workflows**
    
    - Mathematical wave and frequency graphs (Matplotlib + AE).
    - Gradient fills & compositing tricks in AE.
    - 3D neuron simulations (Blender Spike add-on).
    - Probability distribution slicing in Blender using shaders and displacement maps.
    - Brain atlas visualizations with BlenderBrain add-on.
    - Simulation-based neuron network animations using Python, Matplotlib, and Manim.
    
5. **Tips & Key Insights**
    
    - Always render more frames than needed for speed control in AE.
    - Use “time remapping” in AE for syncing with voiceover.
    - Separate building blocks into different layers/files for easier compositing.
    - Use “Screen” blending mode to remove black backgrounds from overlays.


---

## **2. Structured Workflow for Creating an Animation**

Here’s a **pseudo-code style workflow** you can follow/adapt:

```lua
# Step 1: Define Concept & Components
DEFINE project_goal
IDENTIFY core elements (objects, graphs, text, background)

# Step 2: Choose Tools Per Element
FOR each element:
    IF 2D vector/diagram → Illustrator
    IF mathematical/data-driven → Python (Matplotlib/Manim)
    IF 3D object/scene → Blender
    ELSE → After Effects

# Step 3: Create Building Blocks
IF using Python:
    PREPARE data arrays
    CREATE visuals using Matplotlib/Manim
    EXPORT as high-FPS video with black background

IF using Blender:
    MODEL objects
    ADD textures/materials
    ANIMATE camera & objects
    EXPORT as video/sequence

# Step 4: Assemble in After Effects
IMPORT all video layers
SET blending mode to 'Screen' for transparency
SCALE & position elements
SYNCHRONIZE to audio using Time Remapping
APPLY effects (gradients, glows, transitions)

# Step 5: Fine-Tuning
ADJUST timing
APPLY color correction
ADD labels, annotations, or text

# Step 6: Export Final Video
SET output format & resolution
RENDER
```

---

## **3. Tools Used in the Video**

### **Main Animation Tools**

- **Adobe After Effects** (core animation/compositing)
	
- **Python**:
    
    - **Matplotlib** (plotting, math animations)
    - ==**Manim**== (graph theory, certain math animations)
    
- **Blender** (3D modeling & animation)


### **Support Tools**

- **Adobe Illustrator** (vector graphics)

- **Adobe Photoshop** (image editing)
 
- **Adobe Premiere Pro** (video editing)

- **Adobe Audition** (audio cleanup)


### **Custom Add-ons**

- **Blender Spike** (neuron simulation import into Blender)

- **BlenderBrain** (brain atlas import into Blender)

- **Blender Color Maps** (Matplotlib gradients into Blender)


---

## Custom Workflow Diagram: Python → Blender → After Effects

Below is a structured text version of the workflow, styled like a flowchart you might trace visually or recreate in diagram tools:

---

```mysql
Script / Concept
      ↓
Prepare Assets & Components
      • Diagrams, icons (Illustrator)
      • Plots, math-based visuals (Python: Matplotlib / Manim)
      • 3D models, simulations (Blender / custom add-ons)
      ↓
Render Building Blocks
      ● Python exports high-frame-rate videos w/ transparency
      ● Blender renders 3D animations (e.g., neurons, slicing)
      ↓
Import into After Effects
      • Layer videos
      • Set blending = “Screen” to remove black backgrounds
      • Position, scale, sync timing (Time Remapping)
      • Stylize: gradients, masks, glows
      ↓
Assemble & Sync Audio
      • Combine video clips
      • Add narration, music (Premiere Pro if extensive editing needed)
      • Polish audio (Audition)
      ↓
Finalize & Export
      • Fine-tune effects, transitions
      • Render final video

```


### Workflow Highlights & Mapping to Tools

- **Script/Concept**: Define your animation’s purpose and identify components.
    
- **Asset Creation**:
    
    - Use **Illustrator** for vector graphics, diagrams.
        
    - Use **Python (Matplotlib/Manim)** for data visualizations and math-driven animations.
        
    - Use **Blender** (with add-ons like Blender Spike or BlenderBrain) for 3D modeling, neuron simulations, or brain atlas imports.
        
- **Render Building Blocks**: Render intermediate videos with transparent backgrounds and many frames for flexible timing adjustments.
    
- **Compositing in After Effects**:
    
    - Layer everything with “Screen” blending to merge visuals cleanly.
        
    - Use time remapping to sync visuals precisely with narration.
        
    - Apply visual effects like gradients, masks, glows.
        
- **Audio Integration & Editing**: Fine-tune the audio in **Audition** and use **Premiere Pro** for arranging clips and final edits.
    
- **Export**: Render the polished final video.
    

---