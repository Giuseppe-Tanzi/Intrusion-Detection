# Intrusion Detection System
<a target="_blank" href="https://colab.research.google.com/github/giuseppe-tanzi/Intrusion-Detection/blob/main/Intrusion%20Detection.ipynb">
  <img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/>
</a>

Authors:

- Daniele Marini
- Giuseppe Tanzi
- Iulian Zorila

## Problem

Starting from a given video:

- 12 frame/s  (total duration is about 41 secs)
- 320x240 pixels
- 8 bit/pixel (256 gray levels)
- The sequence is compressed by the Radius Cinepak CODEC.

Whereby a person moves at different speed and is shown in various sizes. Moreover, in the last part the subject steals
an object belonging to the scene, replacing it with another one.

## Goal

Development of a software system that, based on automatic video analysis, can detect objects (intruders) that do not
belong to a static reference scene (background) and establish which of such objects are persons.

This is achieved by **background subtraction** and blob (Binary Large Object) labeling process, based upon **blob
features** related to its size.

## Instruments
To accomplish the detection of the intruder different techniques have been employed:
* Background extraction through interpolation (mean or median)
  * The **median** turns out to be more effective for this particular video, as the person is constantly moving, therefore pixel intensities, across the frames, which have high variance won't be picked as eligible values.
* Frame difference with extracted background, trying three distances:
  * [Manhattan distance](https://en.wikipedia.org/wiki/Taxicab_geometry).
  * [Euclidean distance](https://en.wikipedia.org/wiki/Euclidean_distance).
  * [Maximum distance](https://en.wikipedia.org/wiki/Chebyshev_distance).
* Morphology operators to improve the **mask** quality (binary image obtained from difference between frame and background):
  * [Opening](https://docs.opencv.org/4.x/d9/d61/tutorial_py_morphological_ops.html), to get rid of noise, consisting of smaller blobs.
  * [Closing](https://docs.opencv.org/4.x/d9/d61/tutorial_py_morphological_ops.html), to fill holes in the detected intruder.
* Contour extraction:
  * [Find and draw contours](https://docs.opencv.org/3.4/d4/d73/tutorial_py_contours_begin.html)
* Features extraction:
  * [Area](https://docs.opencv.org/4.x/dd/d49/tutorial_py_contour_features.html).
  * [Perimeter](https://docs.opencv.org/4.x/dd/d49/tutorial_py_contour_features.html)

|   Output Example    |
|:-------------------:|
| ![](res/output.gif) | 



