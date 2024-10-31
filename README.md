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
