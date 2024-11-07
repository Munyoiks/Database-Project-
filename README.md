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
