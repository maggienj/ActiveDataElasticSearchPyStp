# ActiveDataElasticSearchPyStp
ActiveData - ElasticSearch17 and Py2.7 setup

Step-1: Install python2.7 <br>
In windows powershell <br>
 new-alias python27 c:\python27\python.exe <br>
 cd c:\ActiveData <br>
 set PYTHONPATH=. <br> 
 python27 -m pip install --upgrade pip <br> 
 python27 -m pip install -r requirements.txt <br> 
 <img src=powershell_python27_req.PNG> <br>

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
<img src=ADQtool.PNG> 
