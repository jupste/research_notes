---
title: OpenRefine
created: '2021-07-05T11:25:00.011Z'
modified: '2021-07-05T12:57:39.417Z'
---

# OpenRefine

OpenRefine is a tool for big data transformations. It can for example fill in missing data, change data types and check if values are within a certain threshold. OpenRefine is accessible either through a browser or via an API call.

The proposed OpenRefine setup for our pipeline consist of a dockerized instance with two volume mountpoints. The other volume is used for transporting the datasets to the OpenRefine instance and also OpenRefine produces the clean datasets to this folder. The other volume is for the instructions OpenRefine will perform on the dataset. The instructions are in JSON format and a user can easily convert tasks performed in the browser interface to JSON format by exporting the history. Since documentation on the API commands is a bit lacking, but there are multiple sources for help using the browser interface, this provides an easy way to generate new instructions.

## Extensions

OpenRefine provides many extensions that provide new functionalities. Installing these as simple as copying a folder to the `/extensions` folder in OpenRefine source. Some useful extensions include RDF output, data statistic generation and geodata processing. The geodata processing extension only works on older OpenRefine versions so to get it working on our instance some coding needs to be done. OpenRefine also provides good instructions on how to write our own extensions so if a need arises this is also an option. Extensions can be added without doing any changes to the source code.

## Database extensions

OpenRefine also provides a way to connect straight to a database. This is done via a database connector. Out of the box OpenRefine provides support for MySQL, PostGres, SQLLite and MariaDB. This can be further expanded by adding new database connectors and doing some coding in the source build. Adding new database connections require changes to the source code. 
