# Produce and Consumer Examples
## Description
As introduced in the previous section,  [***/activemq_clients***](https://github.com/5gmeta/message-data-broker/tree/main/examples/activemq_clients) provides examples how to produce (cits/image) data from a Sensor&Device to the MEC using python AMQP [Qpid Proton](https://qpid.apache.org/proton/index.html) reactor API with ActiveMQ. 

In this section, we will explain in further detail how to implement a data producer. 
Specific examples will then be provided in the following pages of this documentation.

## Required packages
- Linux distribution
- Python version 3.5+
- You have successfully installed [python-qpid-proton](https://pypi.python.org/pypi/python-qpid-proton) - including any of its [dependencies](https://github.com/apache/qpid-proton/blob/master/INSTALL.md)


Refering the examples presented, following are some essential parameters while producing data on the 5GMETA platform:

- ***source_id***: a Unique Identifier to distinguish the source of generated data.
- ***tile***: Tile of the source from where the data is being generated in form of QuadKey code. e.g. 1230123012301230 (must be 18 chars in [0-3])
- ***datatype***: should be one of the allowed datatype [cits, video, image]
- ***sub_datatype***: depends upon on the datatype e.g. cam, denm, mappem



## Generic producer structure

A typical producer will contain the following fields, as it can be seen in the [examples](https://github.com/5gmeta/message-data-broker/blob/main/examples/activemq_clients):

- ***Discovery Registration API*** : This API helps you connect your S&Ds and push data to the MEC within a specified tile.


- Getting tile of the source from its current GPS position: 

```tileTmp = Tile.for_latitude_longitude(latitude=latitude, longitude=longitude, zoom=18) ```

    
- Getting the **message-broker access** from the **MEC** within the **previous tile**:
```
service="message-broker"

messageBroker_ip, messageBroker_port = discovery_registration.discover_sb_service(tile,service)
```

- Getting AMQP **Topic** and **dataFlowId** to **push** data into the **Message Broker**:
```
dataflowId, topic = discovery_registration.register(dataflowmetadata,tile)

opts.address="amqp://"+username+":"+password+"@"+messageBroker_ip+":"+str(messageBroker_port)+":/topic://"+topic

jargs = json.dumps(args)
```

## Usage

Let's take an example of CITS message producer as shown here in [sender.py](https://github.com/5gmeta/message-data-broker/blob/main/examples/activemq_clients/cits_sender_python/sender.py) for reference.

- Pass the latitude and longitude GPS position of your sensor device as shown here in :
```
# Geoposition - Next steps: from GPS device.
latitude = 43.3128
longitude = -1.9750

```
- Replace with your ***metadata*** in this section shown below. 

```
dataflowmetadata = {
    "dataTypeInfo": {
        "dataType": "cits",
        "dataSubType": "json"
    },
    "dataInfo": {
        "dataFormat": "asn1_jer",
        "dataSampleRate": 0.0,
        "dataflowDirection": "upload",
        "extraAttributes": None,
    },
    "licenseInfo": {
        "licenseGeolimit": "europe",
        "licenseType": "profit"
    },
    "dataSourceInfo": {
        "sourceTimezone": 2,
        "sourceStratumLevel": 3,
        "sourceId": 1,
        "sourceType": "vehicle",
        "sourceLocationInfo": {
            "locationQuadkey": tile,
            "locationCountry": "ESP",
            "locationLatitude": latitude,
            "locationLongitude": longitude
        }
    }   
}
```
- Use the sample [content.py](https://github.com/5gmeta/message-data-broker/blob/main/examples/activemq_clients/cits_sender_python/content.py) to generate your messages. Here as you can see the ***msgbody** contains the CITS message.  
```
def messages_generator(num, tile, msgbody='body_cits_message'):
    messages.clear()
    
    #print("Sender prepare the messages... ")
    for i in range(num):        
        props = {
                    "dataType": "cits",
                    "dataSubType": "cam",
                    "dataFormat":"asn1_jer",
                    "sourceId": 1,
                    "locationQuadkey": tile+str(i%4),
                    "body_size": str(sys.getsizeof(msgbody))
                    }

        messages.append( Message(body=msgbody, properties=props) )

```

