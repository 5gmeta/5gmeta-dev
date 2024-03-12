Live data colleted from 5 traffic sensors installed in the city of Versailles

Relevant information in each traffic sensors is:
Time,
Throughput,
OccupancyRate,

Header

    protocolVersion: The version of the protocol used
    messageID: A unique ID for the message
    stationID: The ID of the station that captured the CAM

Traffic_sensors
	
    List current observation for every traffic sensors
	
Traffic sensor
    
    Throughput: Number of vehicles detected every 5 minutes
    OccupationRate: Sum of the travel time for each vehicle for a given time window
    Time: Time of the measurement done by the sensor
