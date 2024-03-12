CAM Messages of a simulation which is running during 1 hour with few hundreds of vehicles.

The CAM dataset contains messages with information captured by Cooperative Awareness Messages (CAM).
Relevant information in each message is:
StationID,
generationDeltaTime,
latitude,
longitude,
speed


Header

    protocolVersion: The version of the protocol used
    messageID: A unique ID for the message
    stationID: The ID of the station that captured the CAM

CAM

    generationDeltaTime: enerationDeltaTime = TimestampIts mod 65 536

basicContainer

    stationType: The type of the station that captured the CAM
    referencePosition:
        latitude: The latitude of the station
        longitude: The longitude of the station

highFrequencyContainer

    heading:
        headingValue: The heading value
    speed:
        speedValue: The speed value
    driveDirection: The drive direction (forward, backward,unavailable)
    vehicleLength:
        vehicleLengthValue: The length of the vehicle
        vehicleLengthConfidenceIndication: Confidence in the vehicle length
    vehicleWidth: The width of the vehicle
    longitudinalAcceleration:
        longitudinalAccelerationValue: The longitudinal acceleration value
        longitudinalAccelerationConfidence: Confidence in the longitudinal acceleration
    accelerationControl: Acceleration control status
    lanePosition: The lane position of the vehicle
