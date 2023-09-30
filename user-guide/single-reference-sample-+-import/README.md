# 🪵 Single Reference Sample + Import

### What are Reference Samples?

TimberID allows you to add reference Timber Samples to your database. Reference Timber Samples are those collected by researchers or related entities whose measurements are used to train models.&#x20;

TimberID uses Reference Timber Samples to train a Variational Inference ML model that predicts isotope ratios for several elements (dO18, dC13, dN15).



## How do I enter a Reference Sample?

There are two options for adding sample data.

1.  You may use the option "Single Reference Sample" under  "Add Sample".\


    <figure><img src="../../.gitbook/assets/TimberID_singlereferencesample.png" alt=""><figcaption></figcaption></figure>

    Single Reference Sample allows you to enter data about one timber sample, including all measurements that may exist at different points on the disc or slice of timber.\

2. You may also use the option "Import Samples" right below "Single Reference Sample"\
   Import Samples allows you to import multiple Samples from a CSV file.

### Adding a Single Reference Sample

<figure><img src="../../.gitbook/assets/TimberID_sample.png" alt=""><figcaption></figcaption></figure>

If you enter a Reference Sample with the TimberID UI, it will record the following items on the first screen:

<table><thead><tr><th width="196">Field</th><th width="135.33333333333331">Required</th><th>What to enter</th></tr></thead><tbody><tr><td>Sample Name</td><td>Required</td><td>Any text that names the sample. TimberID assigns a unique ID independently from this field.</td></tr><tr><td>Status</td><td>Required</td><td>"Completed" if all measurements have been taken.<br>May also be "in transit", "in progress" or "not started" to indicate various progress within a lab. Only "Completed" samples are exported to Earth Engine for research.</td></tr><tr><td>Tree Species</td><td></td><td>The scientific species name of the timber. Please select an entry from the drop-list.</td></tr><tr><td>Origin</td><td></td><td>Should always be "Known" for Reference Samples.</td></tr><tr><td>Collection Site</td><td>Required</td><td>The name of the collection site which may be identical to Municipality (if only one site exists in a Municipality). Can be any text.</td></tr><tr><td>Latitude/Longitude</td><td>Required</td><td>The latitude and longitude representing a location within Brazil that identifies where the tree was harvested for the timber sample. If you are in the south, you must use minus signs.  For example, -3.946713, -53.101942  - Altamira, Pará.</td></tr><tr><td>State</td><td></td><td>The state in which the latitude/longitude exists.</td></tr><tr><td>Municipality</td><td></td><td>The municipality in which the latitude/longitude exists.</td></tr><tr><td>Date Collected</td><td></td><td>For Reference Samples, the date the sample was harvested from a live tree.</td></tr><tr><td>Collected By</td><td>Required</td><td>Whether this timber sample was collected by a third party or the organization itself</td></tr><tr><td>City</td><td></td><td>The city in which the 3rd party collected the sample.</td></tr></tbody></table>

After hitting Next, the following screen appears with additional optional measurements to be recorded:

<figure><img src="../../.gitbook/assets/TimberID_measurements.png" alt=""><figcaption></figcaption></figure>

<table><thead><tr><th width="251.33333333333331">Field</th><th>What to enter</th></tr></thead><tbody><tr><td>Measuring height</td><td>The height in cm off the forest floor where the sample was taken.</td></tr><tr><td>Sample type</td><td>One of "Disc", "Triangular", "Chunk" or "Fiber" to indicate the shape or characteristic of the timber.</td></tr><tr><td>Diameter</td><td>The diameter in cm of the sample.</td></tr><tr><td>AVP</td><td></td></tr><tr><td>Mean Annual Temperature</td><td></td></tr><tr><td>Mean Annual Precipiation</td><td></td></tr><tr><td>Observations</td><td>Free text that indicates any observations or notes about the sample.</td></tr><tr><td>Measurements</td><td>Isotope measurements as recorded by a mass spectrometer.</td></tr><tr><td>  dO18_cel</td><td>delta O18 from cellulose</td></tr><tr><td>  dO18_wood</td><td>delta O18 from wood</td></tr><tr><td>  dN15_wood</td><td>delta N15 from wood</td></tr><tr><td>  N_wood</td><td>N from wood</td></tr><tr><td>  d13C_wood</td><td>delta C13 from wood</td></tr><tr><td>  d13C_cel</td><td>delta C13 from cellulose</td></tr><tr><td>  %C_wood/%C_cel</td><td>the percentage of carbon in wood or cellulose.</td></tr></tbody></table>

Click on the Next button and the final page allows you to review what you have entered. Click "Create Sample" to add the sample to TimberID as below.

<figure><img src="../../.gitbook/assets/TimberID_createSample.png" alt=""><figcaption></figcaption></figure>

### Importing Sample from a CSV file

TimberID also allows you to import many reference samples at once through a csv file. The csv file must:

* Use commas to separate values
* The first row must be column names
* The column names must all be lower case

You may include any columns you wish and while TimberId will not display all of them in the  UI, they will be exported to Earth Engine as features at the latitude/longitude indicated.

#### Required Import Fields

Importing does require the following columns with respective validation rules.

<table><thead><tr><th width="168">Field</th><th width="168">Validation</th><th width="100">Required</th><th>Description</th></tr></thead><tbody><tr><td>code</td><td>none</td><td>Y</td><td>The unique id for a sample that has potentially multiple rows (one for each measurement)</td></tr><tr><td>trusted</td><td>['trusted', 'unknown', 'untrusted']</td><td>Y</td><td>'trusted' samples indicate a reference sample. <br>'untrusted' samples are those intended to run under origin verification. <br>'unknown' are those that do not have a precise lat/lon</td></tr><tr><td>lat</td><td>>=-90, &#x3C;=90</td><td>Y</td><td></td></tr><tr><td>lon</td><td>>=-180, &#x3C;=180</td><td>Y</td><td></td></tr><tr><td>d18O_cel</td><td>>=20, &#x3C;=32</td><td>N</td><td></td></tr><tr><td>d18O_wood</td><td>>=20, &#x3C;=32</td><td>N</td><td></td></tr><tr><td>d15N_wood</td><td>>=-5, &#x3C;=15</td><td>N</td><td></td></tr><tr><td>n_wood</td><td>>=0, &#x3C;=1</td><td>N</td><td></td></tr><tr><td>d13C_wood</td><td>>=-38, &#x3C;=20</td><td>N</td><td></td></tr><tr><td>c_wood</td><td>>=40, &#x3C;=60</td><td>N</td><td></td></tr><tr><td>d13C_cel</td><td>>-35, &#x3C;=-20</td><td>N</td><td></td></tr><tr><td>c_cel</td><td>>=40, &#x3C;=60</td><td>N</td><td></td></tr></tbody></table>

#### Validation Errors

When you import values, if there are errors in your CSV or validation errors, TimberID will create a mirror copy of your input csv along with a new column called 'error' which is filled out for each row that has a validation error.

You can see the full list of potential import errors along with how to fix them, [here](import-errors.md).

#### Example CSV File

You may use the linked file as an example to create a valid import file.

{% file src="../../.gitbook/assets/timberid_example (1).csv" %}
Import Example
{% endfile %}

