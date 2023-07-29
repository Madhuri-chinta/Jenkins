# MUSICSTORE APPLICATION:
-------------------------
* This project requires
    * dotnet 6.0 core
    * nodejs 16
### INSTALLATION OF DOTNET:6.0
-------------------------------
```
sudo apt-get update 
sudo apt-get install -y dotnet-sdk-6.0
sudo apt-get install -y aspnetcore-runtime-6.0
dotnet --version
```
### INSTALLATION OF NODE:16.0
------------------------------
```
curl -sL https://deb.nodesource.com/setup_16.x | sudo -E bash -
sudo apt-get install -y nodejs
node -v
```
### CLONE THE APPLICATION:
---------------------------
```
git clone https://github.com/Madhuri-chinta/MusicStore.git
cd MusicStore/
dotnet restore ./MusicStore/MusicStore.csproj
dotnet build ./MusicStore/MusicStore.csproj 
dotnet test ./MusicStore/MusicStore.csproj 
```
### JAVA INSTALLATION AND EXPORT PATH:
---------------------------------------
* To run sonarqube we want java(from java-11 to above versions) and export the java path
```
sudo apt update
sudo apt install openjdk-17-jdk -y
export PATH=/usr/lib/jvm/java-17-openjdk-amd64/bin:$PATH
```
## TO SETUP SONARCLOUD:
------------------------
* Firstly install docker 
```
curl -fsSL https://get.docker.com -o install-docker.sh
sh install-docker.sh --dry-run
sudo sh install-docker.sh
sudo usermod -aG docker ubuntu
exit
relogin
docker info
```
* To pull 'sonarqube:latest' image from docker hub and create docker container with that image
* After go to web and give '<instance public ip:container port number>' open sonar cloud page
* After  give username and password enter into that page and go to my account generate one user token,that token give some secret code 
* After go to projects create one project with project key and enter into the 'Set up project for Clean as You Code',select 'use the global setting 'option,created the project
* After analyze our repository 'locally' with steps
  => In first step 'PROVIDE TOKEN'select the 'use existing token' and give the secrete code of existing token
  => In second step 'RUN ANALYSIS ON YOUR PROJECT' select the '.NET' and choose our build tool '.NETCore' after 
    come
    * Scanner .NET Core Global Tool command:
      ```
      dotnet tool install --global dotnet-sonarscanner
      ```
    * Execute the Scanner commands:
      ```  
      dotnet sonarscanner begin /k:"<projectkey>" /d:sonar.host.url="<url of sonarcloud>"  /d:sonar.token="<secrete code of token>"
      dotnet build /home/ubuntu/MusicStore/MusicStore.sln
      dotnet sonarscanner end /d:sonar.token="<secrete code of token>"
      ```



