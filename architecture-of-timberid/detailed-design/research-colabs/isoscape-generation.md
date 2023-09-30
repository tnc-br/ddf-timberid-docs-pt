# Isoscape Generation

Last Updated: 2023-09-27

## Overview

Find the Colab at: [https://colab.research.google.com/github/tnc-br/ddf\_common/blob/main/generate\_isoscape.ipynb](https://colab.research.google.com/github/tnc-br/ddf\_common/blob/main/generate\_isoscape.ipynb)

generate\_isoscape.ipynb under ddf\_common generates isoscapes from a TensorFlow model. This is specifically built to work with the variational inference deep learning model described in [Model Training (Variational Inference)](model-training-variational-inference.md).

A good place to start is to run the notebook with the default isoscape ("/content/gdrive/MyDrive/amazon\_rainforest\_files/variational/model/demo\_isoscape\_model.tf" and "/content/gdrive/MyDrive/amazon\_rainforest\_files/variational/model/demo\_isoscape\_model.pkl") and run each cell in order, observing the outputs.

The last cell of code under "Import Tensorflow model and scalers" saves the isoscapes to a geotiff named according to `OUTPUT_RASTER_NAME` specified at the top of the file. To get the full path, run the following in a Colab cell:

```notebook-python
raster.get_raster_path(OUTPUT_RASTER_NAME+".tiff")
```

Generated rasters can be imported into the [Validation Pipeline](validation-of-isoscapes.md).
