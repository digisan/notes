## install mongodb via docker

1. > docker pull mongo
2. > docker run -d --restart=always --name mongo-db -v ~/mongo/data:/data/db -p 27017:27017 mongo

## connect compass to remote server

### dangerous!, DO NOT use this in production

1. sudo nano /etc/mongodb.conf
2. bind_ip = 127.0.0.1 => bind_ip = 0.0.0.0 or bind_IP = 127.0.0.1, SERVER
3. sudo systemctl restart mongod.service

### safe, use this

e.g. `ssh -fN -l ubuntu -i ./ssh-key.pem -L 9999:localhost:27017 [remote public ip]`

ssh with pem: `9999` is your local port mapped to remote port, localhost is remote 'localhost', `remote public ip` is remote public IP