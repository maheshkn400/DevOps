# Integate Sonarqube On Jenkins
#### Pre-Requirment
- [SonarQube Server](./sonarqube_installation.md)
- [Jenkins Sever](../Jenkins/Jenkins_installation.md)

#### Integatation

Login to Jenkins server and install sonarqube scanner.
~~~sh
wget https://binaries.sonarsource.com/Distribution/sonar-scanner-cli/sonar-scanner-cli-3.2.0.1227-linux.zip
unzip sonar-scanner-cli-3.2.0.1227-linux.zip
mv sonar-scanner-3.2.0.1227-linux /opt/sonar_scanner
~~~
Set SonarQube server details in sonar-scanner property file: `/opt/sonar_scanner/conf/sonar-scanner.properties`
~~~sh
vi /opt/sonar_scanner/conf/sonar-scanner.properties
# uncomment the following and provide details as follows
sonar.host.url=http://<SONAR_SERVER_IP>:9000
~~~
Login to Jenkins GUI console and install `SonarQube scanner` plugin
- Jenksins Dashboard `Manage Jenkins` > `Manage Plugins` > `Avalable` > `SonarQube Scanner for Jenkins`

Configure SonarQube scanner home path
- Jenkins Dashboard > `Manage Jenkins` > `Global Tool Configuration` > `SonarQube Scanner`
  - Name : `sonar_scanner`
  - uncheck `install automatic`
  - SONAR_RUNNER_HOME : `/opt/sonar_scanner`

Configure SonarQube server name and authentication token
- Jenkins Dashboard > `Manage Jenkins` > `Configure Systems` > `SonarQube Servers`
Name : `SonarQube`
ServerURL : `http://<Sonarqube_server_ip>:9000/sonar`

Server authentication token To Get Authentication code follow below steps.
- Login to SonarQube server as a admin `My Account` > `Security` > `Generate Token`

Create a `free style` job to test SonarQube. Provide below sonar properties details in the job under build

- Soruce Code Management
 - git
   - Repositories
     - Repository URL : https://github.com/maheshkn400/SimpleCustomerApp
- Build
  - Execute SonarQube Scanner > Analysis properties (it is mandatary).
    - sonar.projectKey=mkn400
    - sonar.projectName=mkn400Demo
    - sonar.projectVersion=1.0
    - sonar.sources=/var/lib/jenkins/workspace/$JOB_NAME/<PROJECT_NAME>/src

Execute job to get analysis report.
