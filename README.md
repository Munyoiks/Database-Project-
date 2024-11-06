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

