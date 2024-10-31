Disaster Preparedness and Response Database Tables.
1. VULNERABLE_AREAS

area_id (Primary Key, INTEGER)
area_name (VARCHAR(100))
population_count (INTEGER)
last_assessment_date (timestamp)

2. HAZARD_TYPES

hazard_id (Primary Key, INTEGER)
hazard_name (VARCHAR(100))
description (varchar(200))
seasonal_pattern (VARCHAR(100))
