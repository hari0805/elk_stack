This notebook is used to load data  to Elasticsearch in efficient way using cloud api, cloud username and password, and to localhost. this file having three classes.

# Using Elk_api class

If you are trying to load data using cloud api, then use Elk_api() class.

first you need to get api key from elasticsearch by executing these lines of code in dev tools in Kibana.

curl to get api details

POST /_security/api_key?pretty
{

  "name": "python_api",

  "role_descriptors": {}

}

then after getting api details you need to create configuration file with extension .ini and pass it to the Elk_api class

# Use the below mentioned lines to create .ini file

[DEFAULT]
cloud_id = DEPLOYMENT_NAME:CLOUD_ID_DETAILS
apikey_id = API_KEY_ID
apikey_key = API_KEY_DETAILS

Example:
ek = Elk_api('example.ini')
ek.load_data('file_name.csv', 'index_name')

# Using Elk_cloud class

If you are trying to load data using cloud username and password, then use Elk_cloud() class.

Similar to api class you nedd to create .ini file and pass it to the class 

Use the below mentioned lines to create .ini file

[ELASTIC]
cloud_id = DEPLOYMENT_NAME:CLOUD_ID_DETAILS
user = elastic
password = LONGPASSWORD

Example:
ek = Elk_api('example.ini')
ek.load_data('file_name.csv', 'index_name')

# Using Elk_local class

If you are trying to load data to localhost, then use Elk_local() class.

You need to pass localhost --http://localhost:9200

Example:
ek = Elk_api('http://localhost:9200')
ek.load_data('file_name.csv', 'index_name')
