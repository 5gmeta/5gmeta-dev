
In this page, we introduce examples which can be run for image data type.

## Steps to run examples

The examples can be found in the folder [examples/message-data-broker/image_sender_python](https://github.com/5gmeta/5gmeta-dev/tree/main/examples/message-data-broker/image_sender_python).

Similarly to the [C-ITS sender example](cits-sender-message-data-broker.md), you need to configure the address of the data broker.

Then, in one terminal window run:

    python3 sender.py

    or

    python3 sender_with_sd_database_support.py

Depending if your are running your S&D connected to an database or not

You can put the images you are going to send in sample_images folder.

If you want to do some debugging and check if your messages are being sent run in another terminal to receive messages (you have to modify address.py in order to put the appropriate ip, port and topic given by your message broker) :

    python receiver.py

Use the ActiveMQ admin web page to check Messages Enqueued / Dequeued counts match. 

You can control which AMQP server the examples try to connect to and the messages they send by changing the values in config.py

You have to take into account that any modification made on dataflowmetadata must be applied too into the content.py file in order to generate the appropriate content.

## Other resources
***The initial example for this client is at the [link](https://github.com/apache/activemq/tree/main/assembly/src/release/examples/amqp/python)***

    - *https://qpid.apache.org/releases/qpid-proton-0.36.0/proton/python/docs/tutorial.html*
    - *https://access.redhat.com/documentation/en-us/red_hat_amq/6.3/html/client_connectivity_guide/amqppython*
