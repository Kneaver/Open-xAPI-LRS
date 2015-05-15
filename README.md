express-xAPI-LRS
================

An xAPI LRS Mockup for Express-js
Licence: MIT
Requires only NodeJS, optional use of MongoDB if present.

2015-05-15 Update. I restarted this dormant project because I really need a simple to install xAPI LRS. AFAIK today we have two vendors of LRS SAAS, one vendor with an open source solution but in PHP and under GPL licence which could be too constraining for anyone doing commercial work. 

My goal is really to produce a strict LRS, no analytics, no HTML will be served in the first iteration. Anyone willig to have a parallel project to take the data, possibly via a specific API and use it to display some analytics is welcom.

It's a node project. Setup goes as follow

1. Install NodeJS (see https://nodejs.org/ )
2. Download the project using clone, git or simply a zip
3. start a shell in the directory of the project (same for every OS)
4. npm install
5. node app.js
you should get
----------- LRS Starting --------------
Express xAPI LRS listening on  http:RADIAL26:3000 uptime 0
you have an LRS :)

The project is organized as follow

app.js : a main application instanciate an express http server
routes/index.js : all the requests corresponding to all the xAPI endpoints
lib/LRS-JSON.js : a simplified memory based LRS with regular backup on a text file. This is largely sufficient for IDs building their iteractions with xAPI. Having simply text files allows also to run several scenarios.
lib/LRS-MongoDB.js : a real implementation with MongoDB as long persistency service.
lib/LRS-proxy.js : will echo every call to another LRS possibly behind a firewall. This is what will be used for Kneaver.com.

Command line allows to change several default parameters

--port change the port number
--mongodb connection_string start an LRS backed on mongoDB. Connection string will be used to open the connection to mongoDB.
--json path change the default path to the json backup file. The LRs wil start by loading the file it it exists.
--save interval set the interval for backups of pure memory LRS. An interval of 0 disable the save. 
--proxy endpoint

That's all folks, simple, lightweight, likely not fully compliant before some time.
