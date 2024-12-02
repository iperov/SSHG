# Simple Synthetic Head Generator (SSHG)

Generate your own synthetic human head dataset for free using Blender software. The dataset can be used in face analyzation, model pretraining, and other machine learning tasks.

![Picture](https://github.com/iperov/SSHG/blob/master/doc/logo.jpg)

## Limitations

The facial model has extensive deformations to ensure high variability. This makes it difficult to adapt eyes and teeth for such deformations. 
Therefore, eyes and teeth are not present in the 3D model. You cannot use the dataset for tasks that require eyes or teeth, for example relighting. A random background is drawn instead.

## Random background

The simplicity is that I don't need to draw real world environments, real hats, real glasses, real clothes, and other things.
Random pictures from the real world that don't contain faces (not noise) are enough for the neural network to ignore everything but the head or face itself.

## Example results

Currently, the effectiveness of dataset for real-world tasks is unproven. Feel free to train the models and post your results in Issues section.

# Requirements

Blender 4.2 or higher. No additional dependencies or plugins required.

# Installation

For ease of use, a ready-made *one-click to run* archive for Windows is available [here](https://github.com/iperov/SSHG/releases), containing:

1) Blender 4.2 Portable

2) Project folder 

3) .bat files

# User manual

## Start rendering without Blender UI

**run SSHG_render.bat**       - infinite render using current settings. The output will be placed in SSHG\render\

**run SSHG_render_CUDA.bat**  - same + override render device to CUDA

## Change the settings

1) run **SSHG_blender.bat**

2) change SSHG settings in the SSHG tab

3) change device settings in Edit -> Preferences -> System

3) save the project

4) close Blender

## SSHG tab settings

![Picture](https://github.com/iperov/SSHG/blob/master/doc/SSHG_tab.png)

### Resolution

Output square resolution of all images. Default: 1024

### Face coverage

Increases facial coverage of the output image in all directions from the center. Default: 2.80

### Face Y offset

Shifts the face along the Y axis of the output image plane. Default: -0.14

### Face Y axis offset

Shifts the yaw-axis around which the head spins. With this parameter, the face can be aligned similar to classic umeyama-align by 2D Landmarks, or rotated around the center of the head. Default: 0.0

### Allow simulation

Allows hair simulation.

### Allow random occlusion

Allows facial occlusions with random backgrounds shaped like hands, microphones, glasses, cigarettes, and the like.

### Allow random glare

Add glare to HEAD and SKIN modes with random probability.

### Output dir 

Name of output dir relative to .blend root dir.

### Output types

Check the checkboxes for the desired output types.

### [Single] button

Render single.

### [Infinite] button

Render infinite. UI will not unlock.

## Output type examples

HEAD

![Picture](https://github.com/iperov/SSHG/blob/master/doc/type_examples/HEAD.jpg)

HEAD_DEPTH 

Center head towards cam +15cm = 1.0
Center head towards cam -15cm = 0.0

![Picture](https://github.com/iperov/SSHG/blob/master/doc/type_examples/HEAD_DEPTH.jpg)

HAIR

Hair-only on transparent background.

![Picture](https://github.com/iperov/SSHG/blob/master/doc/type_examples/HAIR.jpg)

SKIN

![Picture](https://github.com/iperov/SSHG/blob/master/doc/type_examples/SKIN.jpg)

SKIN_DEPTH

![Picture](https://github.com/iperov/SSHG/blob/master/doc/type_examples/SKIN_DEPTH.jpg)

SKIN_EM_MASK

![Picture](https://github.com/iperov/SSHG/blob/master/doc/type_examples/SKIN_EM_MASK.jpg)

SKIN_NORMAL

![Picture](https://github.com/iperov/SSHG/blob/master/doc/type_examples/SKIN_NORMAL.jpg)

FRONTAL_SKIN_NORMAL

![Picture](https://github.com/iperov/SSHG/blob/master/doc/type_examples/FRONTAL_SKIN_NORMAL.jpg)

SKIN_WF_MASK

![Picture](https://github.com/iperov/SSHG/blob/master/doc/type_examples/SKIN_WF_MASK.jpg)

FRONTAL_SKIN_WF_MASK

![Picture](https://github.com/iperov/SSHG/blob/master/doc/type_examples/FRONTAL_SKIN_WF_MASK.jpg)

HAIR_MASK

![Picture](https://github.com/iperov/SSHG/blob/master/doc/type_examples/HAIR_MASK.jpg)

BEARD_MASK

![Picture](https://github.com/iperov/SSHG/blob/master/doc/type_examples/BEARD_MASK.jpg)

EYEBROWS_MASK

![Picture](https://github.com/iperov/SSHG/blob/master/doc/type_examples/EYEBROWS_MASK.jpg)

EYELASHES_MASK

![Picture](https://github.com/iperov/SSHG/blob/master/doc/type_examples/EYELASHES_MASK.jpg)

OCCLUSION_MASK

![Picture](https://github.com/iperov/SSHG/blob/master/doc/type_examples/OCCLUSION_MASK.jpg)

JSON_DATA

```python
{
    "resolution" : 1024,
    
    "face_coverage": 2.8,
    
    "face_y_offset": -0.14,
    
    "face_y_axis_offset": 0.0,
    
    "pitch": -7.898,   # Head pitch relative to view in degrees.
                       # Looking up is +90, straight is 0, down is -90.
                                   
    "yaw": -96.860     # Head yaw relative to view in degrees.
                       # Looking left (from view) is -90, straight is 0, right is +90.
                                   
                       # no roll, because it is always zero
                                   
    "landmarks": {  # name : pos dict.
        "l_eye_l_corner": [676.218, 469.937], # x,y from top-left corner
        "l_eye_r_corner": [595.341, 486.307],
        "r_eye_l_corner": [495.657, 489.591],
        "r_eye_r_corner": [407.453, 478.049],
        "nose_tip": [584.718, 593.121],
        "nose_l_corner": [607.680, 599.532],
        "nose_r_corner": [510.877, 604.725],
        "mouth_l_corner": [626.172, 707.490],
        "mouth_r_corner": [484.847, 708.083],
        "chin_center": [559.415, 868.429]
    }
}
```

Landmarks example

![Picture](https://github.com/iperov/SSHG/blob/master/doc/type_examples/JSON_lmrks.png)

# Changelog

2025.01.01 Initial release

# Citation

```
@software{SSHG,
  title = {Simple Synthetic Head Generator},
  author = {iperov},  
  url = {https://github.com/iperov/SSHG},  
  year = {2025}
}
```