# 🌳 Background

The Amazon is the world’s largest rainforest, a massive carbon sink, and home to incredible biodiversity. 60% of the Amazon rainforest sits within Brazil’s borders. It is being deforested at an alarming rate, and much of the logging is illegal. To fight the illegal timber trade, there is an increasing need to accurately verify or determine the harvest origin of timber.

### Scientific approach

Stable isotope ratio analysis (SIRA) is being pushed forward as a possible tool towards this problem.

#### What are isotopes?&#x20;

Isotopes are atoms of the same element that have an equal number of protons and an unequal number of neutrons, giving them slightly different weights. They can be divided into two categories—radioactive and stable. Unlike radioactive isotopes, stable isotopes  (such as carbon, nitrogen, oxygen) have a stable nucleus that does not decay. Their abundance, therefore, stays the same over time. Isotopes are present everywhere in the world: in human beings, in animals, in trees. As an organism grows, the 'food' it consumes -and its isotopes- are incorporated into the organisms tissues.&#x20;

* See [Incredible Isotopes](https://www.youtube.com/watch?time\_continue=1\&v=R2XWlhNz6WU\&embeds\_referring\_euri=https%3A%2F%2Fwww-agroisolab-com.filesusr.com%2F\&source\_ve\_path=Mjg2NjY\&feature=emb\_logo\&themeRefresh=1)

#### What is SIRA?&#x20;

Since isotopes are incorporated into organisms' atoms from external sources of the environment they grew up in (eg water from rain), we can measure the ratio of different isotopes in an organism, and trace them back to the environment they raised in. This process is called stable isotope ratio analysis (SIRA). See [Stable isotope ratio analysis testing](https://www.agroisolab.com/the-science-of-sira)

* SIRA leverages the influence of the environment (e.g. precipitation, evaporation, atmospheric pressure) on the chemical composition (e.g. ratios of oxygen, carbon, nitrogen isotopes) of an organism - in this case, of a tree.&#x20;
* By collecting multiple samples from the rainforest, and undertaking SIRA, we can build an isotopic map of the rainforest - what we call isoscapes.&#x20;

In practical terms, isoscapes are GeoTIFFs (a file format which embeds geospatial metadata into image files) that contain isotope ratios across the Brazilian Amazon.

### Opportunity

Based on these isoscapes, we can verify the origin of harvested timber by running a sample of it through the same mass spectrometer analysis (SIRA).&#x20;

* With the results of SIRA, and the claimed sample origin (latitude and longitude) provided by the supplier (legally required in Brazil), we can compare it with the 'map' (isoscapes) and verify if the claimed origin is consistent or not. We do this with a t test which is explained in detail in the [Validation Section](../architecture-of-timberid/detailed-design/research-colabs/validation-of-isoscapes.md).
* The origin verification process enables market actors (e.g. enforcement, Federal Police) to verify if timber was harvested in a region where the supplier has a permit to do so, opening up new opportunities to combat illegal deforestation of the Amazon.

#### Other work

The stable isotopes approach has already been successfully applied to map forests outside Brazil, with significantly lower biodiversity (e.g. Canada), and also in a legal context to prosecute bad actors (e.g. [Lumber Liquidators](https://us.eia.org/press-releases/lumber-liquidators-lies-to-the-public/)).&#x20;

In Brazil, specifically the Amazon forest, the biodiversity is significantly higher and therefore more challenging to generate isoscapes (the maps) with a high precision level. Research institutions have been attempting to do so, but since it relies on collecting reference timber samples (which is time consuming, expensive and requires permits), this approach has a long timeframe and cost.

#### Innovation

Current methods to create isoscapes include [Craig-Gordon](https://acp.copernicus.org/articles/20/11435/2020/) and Kriging interpolation. TimberID innovates on the method of creation of the isoscape through the use of Variational Inference (Deep Learning), and streamlines the inputs to that process (the reference sample data) and the application of those isoscapes against real world test cases (analyzing seized timber).
