CREATE TABLE VulnerableAreas(
areaID INT PRIMARY KEY,
areaName VARCHAR (255),
populationArea INT,
lastChecked DATE );

CREATE TABLE HazardType(
hazardID INT PRIMARY KEY,
hazardName VARCHAR (255),
description VARCHAR(10),
seasonalPattern VARCHAR (255)
);

CREATE TABLE EmergencyContacts(
contactID INT PRIMARY KEY,
organizationName VARCHAR(100),
contactName VARCHAR(100),
rolePosition VARCHAR(50),
phone INT,
email VARCHAR(100)
);

CREATE TABLE TrainingPrograms(
programID INT PRIMARY KEY,
programName VARCHAR(100),
description VARCHAR(100),
targetAudience VARCHAR(100),
durationHours INT,
capacitySession INT,
certificationRequired BOOLEAN,
validityPeriod INT
);

CREATE TABLE IncidentLogs(
    incidentID INT PRIMARY KEY,
    areaID INT,
    hazardID INT,
    incidentDate TIMESTAMP,
    responseTime INT,
    casualties INT,
    resourceDeployed VARCHAR(100),
    lessonsLearned VARCHAR(100),
    FOREIGN KEY (areaID) REFERENCES VulnerableAreas(areaID),
    FOREIGN KEY (hazardID) REFERENCES HazardType(hazardID)
);

CREATE TABLE CommunityPreparedness(
preparednessID INT PRIMARY KEY,
areaID INT,
assessmentDate TIMESTAMP,
lastDrill TIMESTAMP,
nextDrill TIMESTAMP,
FOREIGN KEY (areaID) REFERENCES VulnerableAreas (areaID)
);

INSERT INTO EmergencyContacts(contactID, organizationName, contactName, rolePosition, phone, email)
VALUES
(1, 'St John', 'Alice', 'Matron', '0767888990', 'alice44@stjhn.org'),
(2, 'Fire station', 'Bob', 'Chief', '0743222234', 'chiefbob@gmail.com'),
(3, 'Police', 'Stan', 'Inspector', '0762833458', 'inspstan@gmail.com'),
(4, 'Hospital', 'Ian', 'Doctor', '0794235090', 'docian33@gmail.com'),
(5, 'Ambulance', 'Harvey', 'Nurse', '0722513140', 'harevey3306@gmail.com'),
(6, 'Rescue Services', 'Lara', 'Rescuer', '0792334456', 'lara.rescue@gmail.com'),
(7, 'Red Cross', 'Emily', 'Coordinator', '0741256890', 'emily.rcross@gmail.com'),
(8, 'Mountain Rescue', 'Peter', 'Team Leader', '0782347654', 'p.rescues@gmail.com'),
(9, 'Coast Guard', 'Tom', 'Commander', '0723657890', 'tom@coastguard.com'),
(10, 'Animal Control', 'Diana', 'Specialist', '0774567892', 'diana.ac@gmail.com'),
(11, 'Fire station', 'Karen', 'Deputy Chief', '0734445566', 'karenchief@gmail.com'),
(12, 'Forest Service', 'Mike', 'Ranger', '0755678901', 'm.ranger@gmail.com'),
(13, 'Emergency Management', 'Linda', 'Coordinator', '0721567893', 'linda management@gmail.com'),
(14, 'Search and Rescue', 'John', 'Coordinator', '0794345678', 'j.rescues@gmail.com'),
(15, 'City Health Department', 'Nina', 'Nurse', '0734556677', 'nina33076@gmail.com');


INSERT INTO TrainingPrograms (programid, programname, description, targetaudience, durationhours, capacitysession, certificationrequired, validityperiod)
VALUES 
    (1, 'Fire Safety', 'Basic fire response', 'Community', 3, 20, TRUE, 24),
    (2, 'Flood Preparedness', 'Flood risk management', 'Emergency Staff', 5, 25, FALSE, 12),
    (3, 'CPR and First Aid', 'Cardiopulmonary resuscitation and basic first aid', 'General Public', 4, 30, TRUE, 36),
    (4, 'Earthquake Readiness', 'Preparedness for seismic events', 'School Staff', 6, 15, TRUE, 24),
    (5, 'Evacuation Training', 'Safe evacuation procedures', 'Office Workers', 2, 40, FALSE, 12),
    (6, 'Search and Rescue', 'Introduction to search and rescue techniques', 'Rescue Teams', 8, 20, TRUE, 24),
    (7, 'Hazardous Materials Handling', 'Safety around hazardous materials', 'Industrial Workers', 7, 25, TRUE, 12),
    (8, 'Cybersecurity Basics', 'Protection against cyber threats', 'IT Staff', 3, 30, FALSE, 18),
    (9, 'Water Safety', 'Preventing and responding to water accidents', 'Lifeguards', 4, 20, TRUE, 36),
    (10, 'Child Safety', 'Safety protocols for working with children', 'Teachers', 3, 40, FALSE, 24),
    (11, 'High-Rise Evacuation', 'Evacuation training for high-rise buildings', 'Corporate Employees', 2, 50, FALSE, 12),
    (12, 'Disaster Communication', 'Effective communication during disasters', 'Emergency Responders', 5, 20, TRUE, 24),
    (13, 'Basic First Responder', 'Introductory training for first responders', 'Volunteers', 6, 25, TRUE, 18),
    (14, 'Wildfire Management', 'Techniques for wildfire management', 'Forest Rangers', 6, 15, TRUE, 24),
    (15, 'Mental Health Support', 'Providing mental health support in crises', 'Counselors', 4, 30, FALSE, 24);

    
INSERT INTO HazardType(hazardID, hazardName, description, seasonalPattern)  
VALUES 
    (1, 'bushfire', 'biological', 'summer'),
    (2, 'desertification', 'climate', 'summer'),
    (3, 'earthquake', 'geological', 'spring'),
    (4, 'landslide', 'geological', 'winter'),
    (5, 'tsunami', 'geological', 'any Season'),
    (6, 'flood', 'hydrological', 'spring'),
    (7, 'cyclone', 'meteorological', 'summer'),
    (8, 'drought', 'climate', 'any Season'),
    (9, 'volcanic eruption', 'geological', 'any Season'),
    (10, 'avalanche', 'geological', 'winter'),
    (11, 'heatwave', 'climate', 'summer'),
    (12, 'cold wave', 'climate', 'winter'),
    (13, 'tornado', 'meteorological', 'spring'),
    (14, 'hailstorm', 'meteorological', 'spring'),
    (15, 'coastal erosion', 'geological', 'any Season'),
    (16, 'wildfire', 'biological', 'summer'),
    (17, 'sinkhole', 'geological', 'any Season'),
    (18, 'blizzard', 'meteorological', 'winter'),
    (19, 'sandstorm', 'meteorological', 'summer'),
    (20, 'ice storm', 'meteorological', 'winter');

  INSERT INTO IncidentLogs (areaID, hazardID, incidentDate, responseTime, casualties, resourceDeployed, lessonsLearned) VALUES  
(101, 1, '2024-02-15 14:30:00', 15, 0, 'Fire Trucks, Water Tankers', 'Improve fire alarm system'),
(102, 2, '2024-03-20 08:45:00', 30, 3, 'Ambulances, Medical Team', 'Need for better road access'),
(103, 3, '2024-04-12 11:20:00', 45, 12, 'Helicopters, Rescue Boats', 'Enhance flood warning system'),
(104, 4, '2024-05-03 16:10:00', 10, 0, 'Hazmat Team, Protective Gear', 'Increase chemical storage training'),
(105, 5, '2024-06-28 09:50:00', 60, 1, 'Fire Brigade, Paramedics', 'Regular equipment maintenance needed'),
(106, 6, '2024-07-15 22:00:00', 20, 0, 'Police Units, Traffic Control', 'Enhance public communication channels'),
(107, 1, '2024-08-11 19:25:00', 35, 5, 'Evacuation Buses, Firefighters', 'Faster evacuation plans required'),
(108, 2, '2024-09-07 07:15:00', 25, 2, 'Drones, Search Dogs', 'Improved coordination among teams'),
(109, 7, '2024-10-21 14:00:00', 40, 10, 'Relief Supplies, Medical Camps', 'Better disaster preparedness'),
(110, 8, '2024-11-02 03:35:00', 55, 8, 'Engineering Team, Support Vehicles', 'Reinforce infrastructure'),
(101, 3, '2024-12-19 13:10:00', 50, 0, 'Pumps, Flood Barriers', 'Upgrade drainage systems'),
(102, 9, '2025-01-30 06:40:00', 65, 4, 'Helicopters, Search and Rescue Teams', 'Review evacuation protocols'),
(103, 10, '2025-02-25 17:55:00', 5, 0, 'Bomb Squad, K9 Units', 'Improved surveillance measures'),
(104, 11, '2025-03-12 20:20:00', 75, 6, 'Tents, Water Purification Units', 'Increase stockpile of emergency goods'),
(105, 12, '2025-04-08 12:30:00', 12, 0, 'Fire Drones, Surveillance Cameras', 'Early detection system upgrade');

INSERT INTO CommunityPreparedness (preparednessID, areaID, assessmentDate, lastDrill, nextDrill)
VALUES
(1, 101, '2024-10-01 14:00:00', '2024-09-15 10:00:00', '2024-12-15 10:00:00'),
(2, 102, '2024-10-05 09:30:00', '2024-08-25 16:00:00', '2024-11-20 14:00:00'),
(3, 103, '2024-11-01 13:45:00', '2024-10-10 11:00:00', '2024-12-05 15:30:00'),
(4, 104, '2024-10-20 08:00:00', '2024-09-01 14:00:00', '2025-01-10 09:00:00'),
(5, 105, '2024-11-15 15:15:00', '2024-10-05 13:00:00', '2025-02-20 14:00:00'),
(6, 106, '2024-11-18 10:30:00', '2024-09-20 09:00:00', '2024-12-22 11:00:00'),
(7, 107, '2024-10-25 14:45:00', '2024-07-15 10:30:00', '2025-01-18 15:00:00'),
(8, 108, '2024-09-12 16:00:00', '2024-08-01 14:00:00', '2024-12-05 09:30:00'),
(9, 109, '2024-11-05 11:15:00', '2024-10-02 13:00:00', '2024-12-25 10:45:00'),
(10, 110, '2024-11-20 09:00:00', '2024-09-10 16:15:00', '2025-01-30 08:00:00');
