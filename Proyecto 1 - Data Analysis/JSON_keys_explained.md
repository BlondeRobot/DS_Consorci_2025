General and Identification Information

CCSDS_OMM_VERS: Version of the CCSDS Orbital Mean-Elements Message format
COMMENT: Indicates how this data was generated ("GENERATED VIA SPACE-TRACK.ORG API")
CREATION_DATE: When this data set was created (June 19, 2020)
ORIGINATOR: Organization that produced this data ("18 SPCS" - 18th Space Control Squadron)
OBJECT_NAME: The satellite's name (STARLINK-1506)
OBJECT_ID: The international designator (2020-038T), indicating launch year (2020), launch number (038), and object piece (T)
NORAD_CAT_ID: The catalog number (45747) assigned by NORAD/US Space Command
CLASSIFICATION_TYPE: Security classification ("U" for unclassified)
ELEMENT_SET_NO: Sequential number assigned to this element set (999)
OBJECT_TYPE: Type of object ("PAYLOAD" indicating an active satellite, not debris)
COUNTRY_CODE: Country of origin (US)
RCS_SIZE: Radar Cross Section size (null in this case, indicates no data)

Reference Frame Information

CENTER_NAME: Central body the satellite orbits ("EARTH")
REF_FRAME: Reference frame used for the orbital elements ("TEME" - True Equator Mean Equinox)
TIME_SYSTEM: Time system used for epoch and time calculations ("UTC")
MEAN_ELEMENT_THEORY: Orbital theory used to calculate the elements ("SGP4" - Simplified General Perturbations 4)
EPHEMERIS_TYPE: Type of ephemeris used (0 indicates SGP4/SDP4 model)

Orbit Parameters

EPOCH: The reference time for which these orbital elements are valid (June 19, 2020)
MEAN_MOTION: Number of orbits per day (15.89)
ECCENTRICITY: Shape of the orbit (0.0087515, nearly circular)
INCLINATION: Tilt of the orbit relative to Earth's equator (53.002 degrees)
RA_OF_ASC_NODE: Right Ascension of the Ascending Node, the longitude where the satellite crosses the equator going north (266.3302 degrees)
ARG_OF_PERICENTER: Argument of Perigee, the angle from the ascending node to the closest approach to Earth (69.9474 degrees)
MEAN_ANOMALY: Position of the satellite in its orbit at epoch (221.4733 degrees)
SEMIMAJOR_AXIS: Average distance from the center of the orbit (6683.699 km)
PERIOD: Time to complete one orbit (90.632 minutes)
APOAPSIS: Furthest point from Earth's surface (364.057 km)
PERIAPSIS: Closest point to Earth's surface (247.072 km)
REV_AT_EPOCH: Revolution number at epoch (212)

Perturbation and Drag Terms

MEAN_MOTION_DOT: First derivative of mean motion (0.03503094 revs/day²), indicates orbit decay rate
MEAN_MOTION_DDOT: Second derivative of mean motion (0.01265 revs/day³)
BSTAR: Drag term (0.01007), represents atmospheric drag effect on the satellite

Current Position and Velocity (at epoch)

longitude: Current longitude position (165.93°)
latitude: Current latitude position (-52.91°)
height_km: Current altitude (446.62 km)
velocity_kms: Current velocity (7.64 km/s)

Launch and Status Information

LAUNCH_DATE: When the satellite was launched (June 13, 2020)
SITE: Launch site (AFETR - Air Force Eastern Test Range, Cape Canaveral)
DECAY_DATE: When the satellite deorbited (null, as it was still in orbit)
DECAYED: Whether the satellite has deorbited (0 = no)

SpaceX and File Specific Information

version: Version of the SpaceX API data format ("v1.0")
launch: Reference ID to the launch ("5eb87d46ffd86e000604b389")
FILE: File reference number (2768947)
GP_ID: General Perturbations ID (155985688)
TLE_LINE0: Satellite name line in TLE format
TLE_LINE1: First line of the Two-Line Element set
TLE_LINE2: Second line of the Two-Line Element set
id: SpaceX's unique identifier for this satellite data entry ("5eed7716096e590006985825")

APOAPSIS is the apsis that is farthest from the center of attraction : the high point in an orbit.

PERIAPSIS is the apsis nearest the center of attraction : the low point in an orbit. the point in the path of an orbiting body at which it is nearest to the body that it orbits.

EPHEMERIS book with tables that gives the trajectory of naturally occurring astronomical objects and artificial satellites in the sky, i.e., the position (and possibly velocity) over time. 

Simplified perturbations models are a set of five mathematical models (SGP, SGP4, SDP4, SGP8 and SDP8) used to calculate orbital state vectors of satellites and space debris relative to the Earth-centered inertial coordinate system. This set of models is often referred to collectively as SGP4 due to the frequency of use of that model particularly with two-line element sets produced by NORAD and NASA.