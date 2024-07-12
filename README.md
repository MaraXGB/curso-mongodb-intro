# Mongo DB 
Course of Mongo DB in atlas, compass and mongo for vscode

## Mongo DB Atlas
1. Sign Up with google or github
2. Fill the fisrt configuration they ask: goal, application type, preferred language
3. Choose plan free
4. Server in Virginia
5. Set a name for the cluster
6. Set username and password for db connection
7. If you will connect with local host set ip address 0.0.0.0/0 with the name LOCALHOST
8. Create cluster.
9. Now you can create a database or use a sample collections.

## Mongo DB Compass
1. Sign In mongo atlas
2. Enter in connect on the database previus created on mongo atlas
3. choose Compass
4. Download compass if you don´t haved yet
5. Open compass and create a new connection 
6. Write the connection string that you find in the connect option on mongo atlas
7. change the password in the connection string with created one on mongo atlas
8. You can change the connection name by disconnecting and in the three points with the connectios save it open the option to connect and to change the name.
9. to filter the data on any data base enter the query inside {}

## Mongo DB VSCode
1. Open any folder where you can save the db on wsl.
2. Create the folder for the project
3. enter to that folder and open code .
4. create in the project a .gitignore file (you can fill it with a template on https://toptal.com/developers/gitignore windows, mac, linux are the most commn).
5. create an other file .editorconfig and fill it with the edit config in this gist: https://gist.github.com/MaraXGB/b87039d4ed463cbb41dfddec284b36d3
6. install the extension "MongoDB for VS Code" on VSCode.
7. If is the first time you install the extension close VSCode an reopened.
8. Now in the lateral bar show a leaf opened and choose the connection string to connect.
9. copy the connection string in connect mongo atlas
10. change the password and connect.
11. You can change the connection name
12. for queries crear a folder src on the project
13. other folder with a descriptive name and add a file "query.mongodb"
14. open the file and write "use("database_name")"
15. put db.collection_name.find //with the query you wanna do.
    example: db.zips.find({ state: "NY" })
16. click on  play button in the top bar on the right on vscode and the extension execute the query.

## Docker
1. download the program in this link https://docs.docker.com/desktop/install/windows-install/
2. When Docker Desktop has intalled opened and make sure in the general setting this option “Use the WSL 2 based engine” is activated.
3. Then in the section “Resources > WSL Integration” make sure this option “Enable integration with my default WSL distro” is activated.

###  Ubuntu
1. 
```sh 
sudo apt-get update 
```
2. 
```sh 
sudo apt-get install \
    ca-certificates \
    curl \
    gnupg \
    lsb-release
```
3. 
```sh
 sudo mkdir -p /etc/apt/keyrings
```
4. 
```sh 
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
```
5. 
```sh 
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```
6. 
```sh 
sudo apt-get update
```
7. 
```sh 
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose-plugin
```
8. 
```sh 
sudo docker run hello-world
```

##  Docker project
1. create file docker-compose.yml
2. In the file docker-compose.yml write the follow config:
```sh
version: "3.9"

services:
  mongodb:
    image: mongo:7.0
    ports:
      - 27017:27017
    environment:
      - MONGO_INITDB_ROOT_USERNAME=root
      - MONGO_INITDB_ROOT_PASSWORD=root123
    volumes:
      - mongo_data:/data/db
volumes:
  mongodata:
```
NOTA: documentation for mongo configuration https://hub.docker.com/_/mongo
3. change the mongo version, view in mongo atlas
4. Create a folder in the project, for example mongo_data, that is the same folder in the configuration volumes.
5. In .gitignore add this folder "mongo_data".
6. To up the docker container go to terminal an execute the comand in the src/02_docker/docker.md file.
7. Go to mongo compass and create a new connection
8. Change the name and the color to indentify
9. Enter in advance connection options 
10. Select General MongoDB por ser local
11. Authentication use the username and the password in the docker-compose.yml file
12. TLS/SSL off
13. Save & conect
14. Now you can start creating your own database

## Docker on VSCode
1. In the connection created con mongo compass copy the connection string.
2. create a new connection in mongo db extension on vscode
3. Change the connection name to identify
4. Create a file inside the folder 02_docker with the name query.mongodb

## MondoDB Operators
 
$inc: -> increment a numeric atribute
      $inc: { number: 2 } -> number is the atribute & 2 is the quantity to increment.

$eq: -> compares equal atributes value
      $eq: { number: 2 } -> number is the atribute & 2 is the number to compare

$ne: -> compares no equal atributes value
      $ne: { number: 2 } -> number is the atribute & 2 is the number of the exception.

$gt: -> grater than a numeric value
     number: { $gt: 2 } -> number is the atribute & grater than 2, it doesn´t include the 2.

$gte: -> grater than equal a numeric value
     number: { $gte: 2 } -> number is the atribute & grater than equals 2, it does include the 2.

$lt: -> less than a numeric value
     number: { $lt: 2 } -> number is the atribute & less than 2, it doesn´t include the 2.

$lte: -> less than equal a numeric value
     number: { $lte: 2 } -> number is the atribute & less than equals 2, it does include the 2.
$regex: 
      //Regex return all match with the string inside / /
      db.inventory.find({ "item.description": { $regex: /line/ }})

      i -> put it after /, includes the words no matter the capitals
      db.inventory.find({ "item.description": { $regex: /LINE/i }})

      $ -> put $  at the end of the string before /, gets all match at the end
      db.inventory.find({ "item.description": { $regex: /line$/ }})

      ^ -> put ^  at the start of the string after /, gets all match at the start
      db.inventory.find({ "item.description": { $regex: /^Single/i }})

      m -> put m after the last /, get match multiline (jump line \n)  
      db.inventory.find({ "item.description": { $regex: /^s/im }})

      











