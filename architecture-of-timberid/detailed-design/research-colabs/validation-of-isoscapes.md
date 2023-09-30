# Validation of Isoscapes

Last Updated: 2023-09-27

## Overview

Colab: [https://colab.research.google.com/github/tnc-br/ddf-isoscapes/blob/typo/validation\_pipeline.ipynb](https://colab.research.google.com/github/tnc-br/ddf-isoscapes/blob/typo/validation\_pipeline.ipynb)

The validation pipeline provides a side-by-side comparison of a generated TimberID isoscape with a baseline (typically external from USP, but not necessarily). Additionally, the validation pipeline runs a series of evaluations, including traditional regression metrics like RMSE and end-to-end metrics that measure TimberID's fraud detection capability under the isoscape like AUC-PR and Recall@Precision=0.95.

After validation, isoscape files are stamped with validation results and then written to the path `raster.RASTER_BASE + "/" + ISOSCAPE_OXYGEN_VARS_FILENAME`.&#x20;

## Notes

* **The current default isoscapes for the validation pipeline are not our best model.** We will update this documentation when we have fully validated results.
* Do not use the "Upload to Google Earth Engine" section of this notebook-- it is deprecated and not guaranteed to work properly. Instead, prefer to upload isoscapes to TimberID from the interactive Colab referenced in [Earth Engine API](../../../user-guide/earth-engine-api.md).
