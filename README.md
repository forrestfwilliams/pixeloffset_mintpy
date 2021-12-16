# Using AutoRIFT and MintPy for Timeseries Pixel Offset Tracking
This repository contains a workflow for landslide velocity estimation using a timeseries pixel offset tracking approach for Sentinel-2 data. In the Jupyter Notebooks in the top level of this repository, we:

1. Request and download and a stack of cropped Sentinel-2 images of the same area that are spaced roughly one year apart
2. Use the [AutoRIFT](https://github.com/nasa-jpl/autoRIFT) to perform cross-correlation pixel offset tracking of all possible image combinations
3. Use the timeseries inversion capabilities of MintPy, to estimate an annual velocity rate for each pixel in the East-West and North-South directions

Each of these steps is contained within a separate notebook. Read on to learn more about each notebook.

A note on environments: To save on disk space, the initial retrevial of Sentinel-2 data is done within the Microsoft Planetary Computer [Planetary Computer Hub](http://planetarycomputer.microsoft.com/) hosted notebook environment. While a Planetary Computer account is needed to access this environment, I believe this part of the workflow can be adapted to as any Sentinel-2 repository that has a STAC API interface. Contact me if this is something you would like work with me on!
MintPy and AutoRIFT have incompatible environments, so steps 2 and 3 must also be run in a separate environments. In the future I plan to create dockerfiles for each environment, but until then the user will need to set up their own environments via conda or another package manager. Connect with me on LinkedIn or Twitter to follow this work!

## Author:
Hi my name is Forrest Williams! I’m passionate about using remote sensing and geospatial data analysis to help solve the world’s environmental challenges. I am currently complete a PhD in Earth Sciences at Massy University in New Zealand, but plan to return home to the U.S. and enter private industry as a data scientist in early 2022.

## Step 1: Download Sentinel-2 Images
**Notebook:** download\_sentinel2.ipynb

**Environment:** [Planetary Computer Hub](http://planetarycomputer.microsoft.com/)

This notebook handles the downloading of Sentinel-2 products that are clipped to the study. Note that you will need to sign up for an account you can use the Planetary Computer Hub environment.

## Step 2: Perform AutoRIFT pixel offset tracking
**Notebook:** autorift.ipynb

**Environment:** General Python geospatial analysis environment with the AutoRIFT package

This step performs the actual AutoRIFT pixel offset tracking. The notebook provided uses the parameters that work well for my study area and Sentinel-2 imagery, but you can find out more about using AutoRIFT [here](https://github.com/nasa-jpl/autoRIFT).

## Step 3: Time-series processing
**Notebook:** autorift\_minty.ipynb

**Environment:** MintPy environment

This notebook performs the time-series SBAS processing using MintPy. If you are not familiar with MintPy I would suggest reading through MintPy’s documentation and examples [here](https://github.com/insarlab/MintPy-tutorial).
