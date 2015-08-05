# MemoryIssues
We have created an iOS hybrid app[Cordova IOS 3.8.0, SQLite(Cordova-SQLite-Storage) 0.8.0 Dev] and noticed that there is huge memory consumption while we perform any CRUD operations.
We tried to debug the app by enabling each feature at a time and found that the memory consumption is high when there is a SQLite plugin call. The memory consumed is never released even after we are idle for few minutes.
To ensure that the memory consumption is from the SQLite plugin, we created a new project which performed the below operations
·         as a single record,
·         as a batch operation,
·         with a loop of n records
·         with a loop of n batches
 
The source code is uploaded,  for the sample project in this repository.
Instruments captured during analysis is also attached, for following operations,
      1. Insert - with a (batch of 100 records each) * 100 loop
      2. Select - with a loop of 100
 
Further analysis: Found the memory consumption was less by 5 to 6 MB if the transactions are not used for db operations.
 
Any help on addressing this memory leak would be highly appreciated.
