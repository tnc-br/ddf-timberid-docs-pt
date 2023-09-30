---
description: Documentation of Colab notebooks intended for researchers and advanced users
---

# 👩🔬 Research Colabs

Last Updated: 2023-09-27

## Background

Very broadly, TimberID consists of a production-oriented web application that delivers insights about illegal logging both in reference to specific timber samples based on stable isotopes and in general. Insights about specific timber samples include fraud detection, which determines the likelihood that a set of isotope measurements from a timber sample originate from a given location. Together with our original research and prior work from leading researchers such as Professor Martinelli of the University of Sao Paulo (USP), these Colab notebooks justify our fraud detection methodology and produce the artifacts (isoscapes) that the fraud detection system requires to function.

For more information, see [high-level-design.md](../../high-level-design.md "mention").

## Data + Model Pipeline

<img src="../../../.gitbook/assets/file.excalidraw (3).svg" alt="End-to-End Research Workflow for Training a Model and Publishing an Isoscape" class="gitbook-drawing">

## Notebooks and Repositories

Our research and fraud detection methodology is concentrated in [DDF Isoscapes](https://github.com/tnc-br/ddf-isoscapes), with helper functions in [DDF Common](https://github.com/tnc-br/ddf\_common), and a small loader shim in [DDF Common Stub](https://github.com/tnc-br/ddf\_common\_stub) to help manage the complexity of dependency management in Colab across multiple repositories. Additionally, [DDF Insights Analytics](https://github.com/tnc-br/ddf-insights-analytics) contains some code that we use to experimentally validate our production logic for TimberID.

<img src="../../../.gitbook/assets/file.excalidraw (4).svg" alt="Flow of Control and Organization of Research Colabs" class="gitbook-drawing">

## DDF Common Stub

The DDF common stub contains the `ddfimport` library, which loads DDF Common for development in Colab by cloning a Git repository and mounting it within the Colab host filesystem. There are two ways to import ddf\_common:

* `ddfimport.ddf_source_control_pane()`
* `ddfimport.ddf_import_common()`

The first method opens a graphical source control pane in the Colab that integrates with GitHub and prompts developers to authenticate with their credentials. This is the best way to iterate on and contribute to the DDF Common code library.

Most users will want `ddfimport.ddf_import_common()` instead, which does not require user interaction but also does not facilitate committing changes to DDF Common.

```python
import sys
!if [ ! -d "/content/ddf_common_stub" ] ; then git clone -b test https://github.com/tnc-br/ddf_common_stub.git; fi
sys.path.append("/content/ddf_common_stub/")
import ddfimport
# ddfimport.ddf_source_control_pane() # Developers use this
ddfimport.ddf_import_common() # Most people will want this
```

## DDF Common

This library contains utility functions that we use across various repositories, including these research Colabs. Key functionality includes:

* Data partitioning
* Fraud determination logic (hypothesis test)
* Raster manipulation
* Isoscape generation from a TensorFlow SavedModel
* Script that uploads isoscapes to EarthEngine
