---
description: >-
  Instructions for ingesting data for training isoscape models and using them to
  generate isoscapes
---

# Data Ingestion

Last Updated: 2023-09-27

_Our codebase is evolving rapidly, so these steps are may go out of date. The team is happy to respond to inquiries._

## Background&#x20;

Running the Data Ingestion notebook is generally the first stage in the sequence of steps required to produce a new isoscape. See [.](./ "mention") for more information.

## Running the Notebook

Find the Colab at: [https://colab.research.google.com/github/tnc-br/ddf-isoscapes/blob/main/data\_ingestion.ipynb](https://colab.research.google.com/github/tnc-br/ddf-isoscapes/blob/main/data\_ingestion.ipynb)

In general, the default options in data\_ingestion.ipynb are what most users will want. Most users will not need to change the vast majority of settings. However, advanced users should note the following:

*   **Known Issue:** Mismatched Projections Lead to Poor-Quality Isoscapes\
    Currently, we have a known issue where the data ingestion pipeline uses GeoTIFFs with mismatched projections to instantiate our tabular dataset:\


    <figure><img src="../../../.gitbook/assets/image (18).png" alt=""><figcaption><p>Visual Depiction of the issue</p></figcaption></figure>

    Until this is fixed, generated isoscapes will not be of the quality that they could be.
* "GOOGLE DRIVE" is currently the only working sample source, so users should strongly prefer that. The "TIMBERID" source is still in the testing stage. When it is fully operational, this will automatically import trusted samples from TimberID as a dataset.
* "ORG\_NAME" for the "TIMBERID" source should correspond to the permissions of the user-- Google users should select "google" and USP users should select "USP"
* Pay attention to errors and warnings in the feature selection stage-- these indicate that any downstream models may not train with all of the expected features, which can result in low-quality isoscapes
* Feature selection can be manually overridden. Users who check the "MANUAL\_OVERRIDE\_COLUMNS" checkbox will eventually see a dialog that provides a list of possible features, with the defaults already checked.\
  \
  Users should select all features in the dialog box that are known for the _entire_ area being modeled (e.g., DEM but not Species, unless generating a Species-specific isoscapes; not date\_collected since we are not attempting to generate isoscapes for a specific timestamp, etc.)\
  ![](<../../../.gitbook/assets/image (10).png>)
* If feature selection is overridden, users will also be asked to select labels. These should correspond to the feature being modeled, typically of the format "dxxE", e.g. d18O:![](<../../../.gitbook/assets/image (11).png>)
* Users may select a partitioning strategy. We partition our data into a training, test, and validation partition to [measure the ability of our models to generalize](https://en.wikipedia.org/wiki/Training,\_validation,\_and\_test\_data\_sets) to unseen data. **Most users will want the FIXED partitioning strategy**, which uses a standardized geospatial split agreed upon between Google researchers and Professor Martinelli of USP to prevent [leakage](https://towardsdatascience.com/data-leakage-in-machine-learning-how-it-can-be-detected-and-minimize-the-risk-8ef4e3a97562), allowing for reliable, standardized isoscape evaluation. Isoscapes are computed with only knowledge of the "train" partition, the (hyper)parameters are adjusted based on performance on the "validation" partition, and isoscape quality is assessed in the "test" partition. As future work, the "train" and "validation" partitions may be merged to allow us to train on more data with [cross-validation](https://en.wikipedia.org/wiki/Cross-validation\_\(statistics\)).\
  ![](<../../../.gitbook/assets/image (12).png>)
* Users may specify GROUPING\_COLUMNS. These columns are used to aggregate data and compute summary statistics for variational inference, Kriging interpolation, and other models (currently: mean, variance, and sample count). The default is to use "lat", "lon", and "Code" for grouping for the variational inference model, or just "lat" and "lon" for XGBoost, Kriging, and Linear Kriging. This groups measurements by location, such that our models attempt to predict the mean and standard deviation of a sample of 5 measurements from the sampling distribution of each Code/tree group (if Code is also selected) at a given location.\
  ![](<../../../.gitbook/assets/image (13).png>)
* Grouping: If KEEP\_GROUPING is checked, the exported rows will have unique values of the grouping columns selected above. If False, the exported rows will still contain the mean, variance, and other statistics for each group, but the original set of rows will be exported without combining any rows. For training the variational inference model, check the box (this is the default). For XGBoost, Kriging, and Linear Kriging, select False.
* Visualize the dataset if you'd like, then run the cells under "Export processed dataset." This will export the partitioned, preprocessed data to Google Drive, which can be used to train models and produce isoscapes with existing models.

<figure><img src="../../../.gitbook/assets/image (17).png" alt=""><figcaption></figcaption></figure>

