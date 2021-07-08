---
attachments: [Clipboard_2021-07-05-10-09-49.png]
title: AIS data
created: '2021-07-05T06:41:12.406Z'
modified: '2021-07-08T08:12:50.948Z'
---

# AIS data

AIS data usually contains the following fields:

| **AIS DATA  (dynamic)** |             |          |                                                                                                                     |
|---------------------|-------------|----------|---------------------------------------------------------------------------------------------------------------------|
| **Field**               | **Type**        | **Required** | **Wrangling operations needed**                                                                                         |
| shipid (MMSI)       | string      | yes      | check no nulls, check no dublicate time/shipid pair. Not really a unique identifier, but dublicates highly unlikely |
| timestamp           | datetime    | yes      | check no nulls, check no dublicate time/shipid pair                                                                 |
| longitude           | float       | yes      | check no nulls, check values between 90, -90, check latlons not on land                                             |
| latitude            | float       | yes      | check no nulls, check values between 180, -180, check latlons not on land                                           |
| heading             | float       | yes?     | if missing calculate from previous entries, values between 0, 360.                                                  |
| speed               | float       | no       | check outliers                                                                                                      |
| navigational status | string/int  | no       | probably none, maybe figure out from ship movements if missing                                                      |
|                     |             |          |                                                                                                                     |
|                     |             |          |                                                                                                                     |
|                     |             |          |                                                                                                                     |
|                     |             |          |                                                                                                                     |
| **AIS DATA  (static)**  |             |          |                                                                                                                     |
| **Field**               | **Type**        | **Required** | **Wrangling operations needed**                                                                                         |
| shipid (IMO)        | string      | yes      | check if matches call sign and shipname                                                                             |
| call sign           | string      | yes      | check if matches id                                                                                                 |
| name                | string      | yes?     | probably none, maybe check spelling errors                                                                          |
| vesseltype          | int         | no       | probably none, maybe map to string type vesseltype name                                                             |
| dimensions          | float array | no       | probably none, maybe check if not an outlier                                                                        |
| system location     | string      | no       | none                                                                                                                |
| navigational system | string      | no       | check if in list                                                                                                    |
| destination         | string      | no       | check spelling errors                                                                                               |
| ETA                 | datetime    | no       | check spelling errors, calculate a more accurate time based on nav data                                             |
| draught             | float       | no       | none                                                                                                                |


By doing some analysis on the data I have also found out that the latitudes and longitudes also jump from place to place in an instance. For example I came across one AIS dataset where several vessels jumped from US east coast to US west coast at regular intervals several times per day. Ship identifiers should be unique so this is probably some kind of programming error. Ship MMSIs are known to cause issues, but I have found no definite reason for this behaviour.

Based on the initial discussions, our project will most likely work on individual ships rather than doing calculations that need information from multiple ships at once. This means that filtering out these outliers is feasible for our purposes. 

Generally speaking the AIS data in the test datasets seems to be a bit lacking. Some of these faults are reflective of the real data sets, such as categorically missing values but some such as short time windows could be solved by aqcuiring larger datasets. As it stands currenlty it is difficult to figure out larger ship voyages since the data is collected at only a couple day timespans. 


If we are doing the weather routing shortest route then probably the most important features for our dataset are: coordinates, heading/course, draught and timestamps. Draught limits the number of paths a ship can take in shallow waters. Draught is not usually updated during the voyage and it can change according to the ship's cargo. Some methods have been deviced that can estimate the current cargo of the ships. These rely on rather crude heuristics such as assuming that if an oil tanker visits a port in a oil producing country, it will most likely exit with a full load.




