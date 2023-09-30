# 🌎 Earth Engine API

{% hint style="info" %}
The interactive colab for using our API can be found in our [ddf\_common github repository](https://colab.sandbox.google.com/github/tnc-br/ddf\_common/blob/main/ddf\_ee\_api.ipynb).
{% endhint %}

Much of the earth engine API is built as wrappers around the Earth Engine Python API which has [a very good tutorial](https://colab.sandbox.google.com/github/google/earthengine-community/blob/master/tutorials/intro-to-python-api/index.ipynb). What the Ddf EE API adds is:

* **Improved usability through automatic authorization of TimberID users**. \
  You do not have to set up your own GCP project to use the API. You only need register with TimberID.\

* **Easy to use APIs to access TimberID entered data**.  \
  All data imported into TimberID is automatically exported to Earth Engine in a FeatureCollection. You can access this data with a single API call.\

* **Easy to use APIs to access important climate data**. \
  Rasters such as digital elevation are surfaced for you as a Python function, allowing you to access them without requiring knowledge of the Earth Engine path.\

* **Performant raster access**. \
  For the rasters we load, there are highly parallel routines for downloading data. You can query raster locations in a bulk query and that will be chunked to many subprocesses for faster downloads.
