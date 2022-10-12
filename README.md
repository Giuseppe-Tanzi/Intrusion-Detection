# Intrusion Detection System

### Problem introduction

Starting from a given video:

- 12 frame/s  (total duration is about 41 secs)
- 320x240 pixels
- 8 bit/pixel (256 gray levels)
- The sequence is compressed by the Radius Cinepak CODEC.

Whereby a person moves at different speed and is shown in various sizes. Moreover, in the last part the subject steals
an object belonging to the scene, replacing it with another one.

<img src="res/Intruder.jpeg" width="376" alt="Frame of replaced obejct">

### Goal

Development of a software system that, based on automatic video analysis, can detect objects (intruders) that do not
belong to a static reference scene (background) and establish which of such objects are persons.

This is achieved by **background subtraction** and blob (Binary Large Object) labeling process, based upon **blob
features** related to its size.