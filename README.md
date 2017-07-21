# ActiveData - ElasticSearch Py Setup in Windows 10
ActiveData - ElasticSearch17 and Py2.7 setup

Step-1: Install python2.7 <br>
In windows powershell <br>
 new-alias python27 c:\python27\python.exe <br>
 cd c:\ActiveData <br>
 set PYTHONPATH=. <br> 
 python27 -m pip install --upgrade pip <br> 
 python27 -m pip install -r requirements.txt <br> 
 <img src=powershell_python27_req.PNG> <br>
 <img src=python27_lib_installed.PNG> <br>

Step-2: Install ES1.7 using this link <br>  
https://github.com/rgl/elasticsearch-setup/releases?after=v2.2.1
( The ES17 from https://www.elastic.co/downloads/past-releases/elasticsearch-1-7-0 ....  was quirky and the service was giving errs to start. so used this https://github.com/rgl/elasticsearch-setup/releases?after=v2.2.1  to easily start the ES service ) <br> 
Step-3: modify config file in ES to add these lines to the top <br> 
script.inline: on <br> 
script.indexed: on <br> 
http.compression: true <br> 
cluster.name: maggie_dev <br> 



Step-3: <br> 
(a) Ensure ElasticSearch service is running <br> 
Goto c:/ElasticSearch171 <br> 
Or open the ElasticSearch Terminal and then run "net start elasticsearch" <br> 
<img src=elasticsearch_service_start.PNG> <br>

(b) Run these steps to access the ActiveData Query Tool <br> 
Open GitBash <br> 
cd c:/ActiveData <br> 
export PYTHONPATH=. <br> 
alias python27=c:/python27/python.exe <br> 
python27 active_data/app.py --settings=resources/config/simple_settings.json <br> 
<img src=ActiveData_start_gitbash2.PNG> <br>

Step-4: <br> 
(a) Open http://localhost:5000 <br> 
You Win should be displayed. <br> 

(b) Access http://localhost:5000/tools/query.html <br> 
You should be able to see the ActiveData Query Tool <br> 
<img src=ADQtool.PNG> <br>

Unit Test Results: <br>
<img src=unittests_1.PNG> <br> <br>
** <a href="unit_test_results.txt">  Unit Test Results are here in this link  </a> **


<br>
<br>

As the next step, we will try to stop the Elastic Search 1.7.1 service and then install Version 5.x and check how it executes for unit testing. <br>
Here is how we stop the elastic search 1.7.1 service. <br>
<img src = ElasticSearch171StopService.PNG> <br> <br>

And then , downloaded this exe to check how it runs ... <br>
https://github.com/rgl/elasticsearch-setup/releases/tag/v5.2.2 <br>
<br>
<strike>full link to the exe <br>
https://github.com/rgl/elasticsearch-setup/releases/download/v5.2.2/elasticsearch-5.2.2-jre-8u121-setup-64-bit.exe   </strike><br>
<br>

Downloaded the above link.... but didn't execute it bcos I thought , I would directly download the latest version from elastic.co itself. <br>
So, here is the direct link for <br>
V5.2.2 https://www.elastic.co/downloads/past-releases/elasticsearch-5-2-2 is the latest as of the time of this writing. <br>
Other latest releases could be found at https://www.elastic.co/downloads/elasticsearch

<br>
Elastic Search 5.2.2 has been installed in a separate directory and then bin/elasticsearch.bat was exectd.  It appears that the elastic service is up and running for version 5.2.2 <br>
elasticsearch_servicestart_522.PNG <br>
<img src=elasticsearch_servicestart_522.PNG> 
<br> (Please ignore the highlight of the localhost:port in the above image... it is just the transportation service that runs in 9300 port which is not of importance.  The following line kicks the HttpServer service in port 9200 and that is what of interest to us.  So , please ignore the highlights in the image ) <br>
Next step.... Run the same unit tests again using ES 5.2.2 service.... <br> 


the configuration for app_dev and all_tests could be done withing PyCharm IDE. I use PyCharm Community Edition. Here is how active_data app_dev configuration would look like, as shown in this screenshot.
<img src = app_dev_configuration_maggie.png> <br> <br>
no changes to the logs tab.

the configuration for all_tests could be done withint PyCharm IDE.  Here is how all_tests configuration would look like, as shown in this screenshot. 
<img src = all_tests_configuration_maggie.png> <br> <br>
no changes to the logs tab
