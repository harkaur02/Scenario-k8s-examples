Scenario 4

Create a DB and run it as sts. Delete PV and PVC 

Solution:
Note: make sure the order of deploying manifest files is as follows:
1. secret.yaml
2. service-headless.yaml
3. sts.yaml

Kubernetes commands:
    kubectl create ns dev-sql
    kubectl apply -f secret.yaml -n dev-sql
    kubectl apply -f service-headless.yaml -n dev-sql
    kubectl apply -f sts.yaml -n dev-sql
    kubectl get all -n dev-sql
To connect to mysql:
    kuebctl exec -it my-sql-0 -n dev-sql -- mysql -uadmin -padmin
    mysql> show databases;
    mysql> use wordpress;
    //commands for mysql create table and insert:
    mysql> CREATE TABLE student (
    student_id INT AUTO_INCREMENT PRIMARY KEY,
    first_name VARCHAR(50) NOT NULL,
    last_name VARCHAR(50) NOT NULL,
    dob DATE
    );

    mysql> INSERT INTO student (first_name, last_name, dob)
            VALUES ('John', 'Doe', '2025-04-01');
    mysql> select * from student;
    mysql> exit
Note: Now after coming out from mysql bash prompt, look onto your specified mountPath (mentioned in sts.yaml). Note that the name of the Database you specified through the sts.yaml file here is naned as 'wordpress', it will be shown as a folder in the specified mountpath. go into the database folder and there you will see the table student and its values.

