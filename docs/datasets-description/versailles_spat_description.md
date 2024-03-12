Signal Phase and Timing (SPaT) Messages of 3 intersection in a simulation which is running during 1 hour.

Relevant information in each message is:
IntersectionID,
LaneId (sub_id),
State,


Header

    protocolVersion: The version of the protocol used
    messageID: A unique ID for the message
    stationID: The ID of the station that captured the CAM

SPAT

    Timestamp: represents the simulation step
    Intersections: List of Intersection covered by SPaT messages
    
Intersection

    Id: Unique Intersection identifier    
    States: List of state for each traffic signal line

State

    sub_id: Identifier of traffic signal line    
    state: Current state of traffic signal
