# 🛠 High Level Design

## **Architecture**

Unlike a traditional three tier architecture, TimberID uses a simplified Backend-as-a-Service architecture whose security rules are expressed in a declarative manner directly on the database. This approach reduces amount of code by eliminating the traditional middle tier layer that performs authorization and domain specific logic.

This  allows a clean separation between front and back end where the front end solely interacts directly with the Firestore database. Most operations can then be made securely, directly from the front end relying on the Firstore Security Rules to safeguard data.

The new model of Backend-as-a-Service does not completely get rid of back end code. In cases where complex offline, asynchronous code or sensitive logic (such as fraud verification) must be run, the typical approach is to connect cloud functions directly to the shared database. Both sides (front end and back end) then listen on state changes to the database, each making changes based on user input (in the case of the front end) or the back end (in the case of complex calculations completing).

The below high level diagram summarizes our approach.

<img src="../.gitbook/assets/file.excalidraw (2).svg" alt="" class="gitbook-drawing">

The front end reads and writes directly to the Sample Database. Backend processes are started from Cloud Triggers which do a variety of tasks, from backend computation of origin verification to exporting all data as Earth Engine features so they may be joined with other geospatial data for analysis.

The architecture can be divided into roughly 4 distinct areas:

1. Client: The client is a web front end that runs locally for participating users. It allows users from multiple organizations to manage their samples and analysis.
2. Server: The  server contains all code and data hosted in the cloud. This includes the database, its associated security rules and backend tasks that analyze data to provide insights on potential deforestation.
3. Earth Engine: Earth Engine is used as both a source for analysis and as a destination where sample data and resulting analysis is stored. Using Earth Engine allows us to perform efficient geospatial queries. Earth Engine is also used as a source for ML features.
4. Variational Inference: The Origin Verification analysis requires isotope maps (isoscapes) that are created using machine learning on Google Colabs. These colabs are a good example of using TimberID reference samples to create data necessary to perform analysis.

The detailed set of components is below:

<table><thead><tr><th width="235">Component</th><th>Capability</th></tr></thead><tbody><tr><td>TimberID Front End</td><td>A typescript web front end that supports importing and exporting reference timber samples.<br>Users may also enter in untrusted timber samples and obtain an analysis of the timber that includes origin verification.</td></tr><tr><td>Security Rules</td><td>Authorization Rules script that ensures that organizations/users cannot alter or read each other's samples</td></tr><tr><td>Sample and Analytics Database</td><td>A NoSQL database that stores both externally measured attributes of timber and computed analysis results.</td></tr><tr><td>Cloud Triggers</td><td>The Cloud Triggers launch functions based on a configurable set of conditions including time based (as in a cron) or when a database Document changes</td></tr><tr><td>Origin Verification</td><td>A Function invoked via a Cloud Trigger when a new untrusted timber sample has been added to the database.</td></tr><tr><td>Earth Engine Export</td><td>A Function invoked via a Cloud Trigger periodically to export all samples of all organizations to Earth Engine.</td></tr><tr><td></td><td></td></tr></tbody></table>

##
