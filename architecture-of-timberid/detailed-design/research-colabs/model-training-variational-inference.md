# Model Training (Variational Inference)

Last Updated: 2023-09-27

## Background

TimberID includes many techniques for generating [isoscapes](https://en.wikipedia.org/wiki/Isoscape) from geospatial point-measurements, ranging from Kriging interpolation to our most best-performing variational inference deep learning model. Of all the alternatives we evaluated, our best results come from predicting the isotope distribution with variational inference and a deep neural network, which appears to be a novel technique for isoscape generation. We focus here on producing isoscapes with variational inference, but the same general principles apply to most of our isoscape models.

## Brief Guide: Model Training

Find the Colab at: [https://colab.research.google.com/github/tnc-br/ddf-isoscapes/blob/main/dnn/variational\_inference.ipynb](https://colab.research.google.com/github/tnc-br/ddf-isoscapes/blob/main/dnn/variational\_inference.ipynb)

Most users should obtain somewhat reasonable predictions out-of-the-box by running the training notebook with the default configuration options after running the [data ingestion notebook](data-ingestion.md) with its default options and export path. However, our machine learning models are still one-off artifacts since we are rapidly iterating on model research. The TimberID processes for producing production-quality models are not automatic. For now, this notebook only attempts to provide a reasonable baseline as a place to start for running model experiments.

A few important, high-level notes:

* Some overfitting is normal, but training loss should not _significantly_ dip below validation loss. Example of a typical loss curve:\
  ![](<../../../.gitbook/assets/image (7).png>)\
  \
  If `loss` drops significantly below `val_loss`, the model has most likely memorized its training set and is unlikely to produce a good isoscape. Common reasons for this are: not enough data, a training distribution that is not diverse enough, training for too many epohcs (overtraining). To mitigate overtraining, the notebook comes with early stoping and a default `patience` setting of 30 epochs.
* For reproducible results, be sure to re-run the cell that contains `tf.keras.utils.set_random_seed(18731)` before each training run. This model is very small, which makes it highly sensitive to initialization.
* We use Xavier initialization but have not performed robust experiments to compare alternatives other than no initialization at all.
* The code under "Run this cell to generate an isoscape" does not appear to be fully functional at this time. For generating isoscapes, prefer the [Isoscape Generation](isoscape-generation.md) notebook instead.





