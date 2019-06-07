# Hướng dẫn cài đặt MongoDB
### Step 1 : Import mongoDB repository
```
sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 7F0CEB10
```
Create a source list file for MongoDB
```
    echo "deb http://repo.mongodb.org/apt/ubuntu xenial/mongodb-org/3.4 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-3.4.list
```
Update the local package repository
```
    sudo apt-get update
```
### Step 2: Install the MongoDB packages

```
    sudo apt-get install -y mongodb-org
```
### Step 3: Launch MongoDB as a service on Ubuntu 16.04
Create a configuration file named mongodb.service in /etc/systemd/system to manage the MongoDB service.
```
    sudo vim /etc/systemd/system/mongodb.service
```
Copy the following contents in the file.
```
    #Unit contains the dependencies to be satisfied before the service is started.
    [Unit]
    Description=MongoDB Database
    After=network.target
    Documentation=https://docs.mongodb.org/manual
    # Service tells systemd, how the service should be started.
    # Key `User` specifies that the server will run under the mongodb user and
    # `ExecStart` defines the startup command for MongoDB server.
    [Service]
    User=mongodb
    Group=mongodb
    ExecStart=/usr/bin/mongod --quiet --config /etc/mongod.conf
    # Install tells systemd when the service should be automatically started.
    # `multi-user.target` means the server will be automatically started during boot.
    [Install]
    WantedBy=multi-user.target
```
Update the systemd service with the command stated below:
```
    systemctl daemon-reload
```
Start the service with systemcl.
```
    sudo systemctl start mongodb
```
Check if mongodb has been started on port 27017 with netstat command:
```
    netstat -plntu
```
Check if the service has started properly.
```
    sudo systemctl status mongodb
```
Enable auto start MongoDB when system starts.
```
    sudo systemctl enable mongodb
```
Stop MongoDB
```
    sudo systemctl stop mongodb
```
Restart MongoDB
```
    sudo systemctl restart mongodb
```
### Step 4: Configure and Connect MongoDB
Open mongo shell

```
    mongo
```
Switch to the database admin
```
    use admin
```

Create the root user
```
    db.createUser({user:"admin", pwd:”password", roles:[{role:"root", db:"admin"}]})
```