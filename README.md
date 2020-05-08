# MariaDB-10.3-Connect-Engine-Docker

This contains **MariaDB 10.3** official docker image with **Connect Engine plugin** installed to support,
**Create JDBC Connect Tables** from **Dremio Virtual Datasets (VDS)**.
MariaDB image is based on **_Ubuntu 18.04 LTS bionic_**.

## Steps to run,
1. Clone the repository.
2. Run **_docker-compose up -d_** command on **_connect-engine_** folder.


In my sample docker-compose.yml file I used, (You can change those if you want..)
* root user password = **root**
* host port = **3336**
* container port = **3306**
* container name = **connect**
* image name = **mariadb-connect:1**
* databases will store on **connect-engine/connectData** folder in the host machine. (volume mapping)


Also,
* I only added **dremio-jdbc-driver.jar** to this sample. 
  * you can put **any jdbc driver** to, **connect-engine/jars/jdbc/** path.
* You can put any jar file that you want to use to connect for **JDBC Connect Tables** and add the path to,
  * **connect.conf** file **connect_class_path** variable by appending a **colon (:)**

**Ex:-**
* You can copy **mongo-jdbc.jar** to the **connect-engine/jars/jdbc/** path
* Edit **connect.conf** file **connect_class_path** variable as,
  * **connect_class_path="/usr/lib/mysql/plugin:/usr/lib/jvm/java-1.8.0-openjdk-amd64/jre/lib/ext/dremio-jdbc-driver.jar:/usr/lib/jvm/java-1.8.0-openjdk-amd64/jre/lib/ext/mongo-jdbc.jar"**
