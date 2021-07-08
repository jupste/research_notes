---
attachments: [Clipboard_2021-07-05-10-09-49.png]
title: AIS data
created: '2021-07-05T06:41:12.406Z'
modified: '2021-07-05T11:04:58.902Z'
---

# AIS data

AIS data usually contains the following fields:

![](@attachment/Clipboard_2021-07-05-10-09-49.png)


By doing some analysis on the data I have also found out that the latitudes and longitudes also jump from place to place in an instance. For example I came across one AIS dataset where several vessels jumped from US east coast to US west coast at regular intervals several times per day. Ship identifiers should be unique so this is probably some kind of programming error. Ship MMSIs are known to cause issues, but I have found no definite reason for this behaviour.

Based on the initial discussions, our project will most likely work on individual ships rather than doing calculations that need information from multiple ships at once. This means that filtering out these outliers is feasible for our purposes. 

Generally speaking the AIS data in the test datasets seems to be a bit lacking. Some of these faults are reflective of the real data sets, such as categorically missing values but some such as short time windows could be solved by aqcuiring larger datasets. As it stands currenlty it is difficult to figure out larger ship voyages since the data is collected at only a couple day timespans. 


If we are doing the weather routing shortest route then probably the most important features for our dataset are: coordinates, heading/course, draught and timestamps. Draught limits the number of paths a ship can take in shallow waters. Draught is not usually updated during the voyage and it can change according to the ship's cargo. Some methods have been deviced that can estimate the current cargo of the ships. These rely on rather crude heuristics such as assuming that if an oil tanker visits a port in a oil producing country, it will most likely exit with a full load.




