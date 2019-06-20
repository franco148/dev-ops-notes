### INSTALLING ELASTICSEARCH & KIBANA
#### Running Elasticsearch & Kibana in Elastic Cloud
- Go to elastic cloud web page
- I will ask you to use AWS or Google Cloud Platform. However AWS already offers a elastic search feature, which has more funtionalities.

#### Connecting to our cluster
- Open the terminal for connecting through it .
- ```curl -u elastic:passoword elasticsearch-endpoint```
- Each time we try to connect, it should show us a different node.
- Fo accessing to kibana just click in the dashboard icon, then we will need to use the created credentials.

#### Installing Elasticsearch on Mac/Linux
- Elasticsearch itself is packaged as a ¨jar¨ file, along with its dependencies such as Apache Lucene.
- Needed at least java 8
- Go to the elasticsearch web page, products and download the file (zip, tar, etc)
- ```tar -zxf elasticsearch.tar.gz```
- Navigate to the directory. It contains Elasticsearch itself and ApacheLucene, and other like log4j.
- There is also a config folder where you can find the configurations
- bin/elasticsearch







