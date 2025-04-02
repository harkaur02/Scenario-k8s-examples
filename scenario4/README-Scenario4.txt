Scenario 4

Create a DB and run it as sts. Delete PV and PVC 

Solution:
Note: make sure the order of deploying manifest files is as follows:
1. secret.yaml
2. service-headless.yaml
3. sts.yaml



commands for mysql create table and insert:
CREATE TABLE student (
    student_id INT AUTO_INCREMENT PRIMARY KEY,
    first_name VARCHAR(50) NOT NULL,
    last_name VARCHAR(50) NOT NULL,
    dob DATE
);


INSERT INTO student (first_name, last_name, dob)
VALUES ('John', 'Doe', '2025-04-01');

