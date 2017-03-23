# ActiveDataElasticSearchPyStp
ActiveData - ElasticSearch17 and Py2.7 setup

Step-1: Install python2.7 
In windows powershell
 new-alias python27 c:\python27\python.exe
 cd c:\ActiveData
 set PYTHONPATH=.
 python27 -m pip install --upgrade pip
 python27 -m pip install -r requirements.txt

Step-2: Install ES1.7 using this link
https://github.com/rgl/elasticsearch-setup/releases?after=v2.2.1
( The ES17 from https://www.elastic.co/downloads/past-releases/elasticsearch-1-7-0 ....  was quirky and the service was giving errs to start. so used this https://github.com/rgl/elasticsearch-setup/releases?after=v2.2.1  to easily start the ES service )
Step-3: modify config file in ES to add these lines to the top
script.inline: on
script.indexed: on
http.compression: true
cluster.name: maggie_dev



Step-3:
(a) Ensure ElasticSearch service is running
Goto c:/ElasticSearch171
Or open the ElasticSearch Terminal and then run "net start elasticsearch"
(b) Run these steps to access the ActiveData Query Tool
Open GitBash
cd c:/ActiveData
export PYTHONPATH=.
alias python27=c:/python27/python.exe
python27 active_data/app.py --settings=resources/config/simple_settings.json

Step-4:
(a) Open http://localhost:5000
You Win should be displayed.

(b) Access http://localhost:5000/tools/query.html
You should be able to see the ActiveData Query Tool

