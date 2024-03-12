Parking Avaialability Messages (PAM) of 2 parking areas in a simulation  which is running during 1 hour.

Relevant information in each message is:
parkingID,
capacity,
occupancy,


Header

    protocolVersion: The version of the protocol used
    messageID: A unique ID for the message
    stationID: The ID of the station that captured the CAM

PAM

    Timestamp: represents the simulation step

    parking: 
        id: Unique identifier of the parking area
        capacity: Total number of avaialable paring slots
        occupancy: Number of occupied parking slots
