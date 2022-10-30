## Installation
You will need to deploy this on a docker swarm environment
After your SWARM env is up and running

### Steps - Docker swarm set up
```shell
sudo apt-get install apt-transport-https ca-certificates curl gnupg-agent software-properties-common -y

sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose -y

docker swarm init --advertise-addr <IP> #On your docker manager node
docker swarm join --token <AUTH_TOKEN> <IP>:2377

```


### Resources needed (I am using only 2 nodes).
500 GB Storage, go as high as you need for this based on your requirements [1 worker node with this is ok if ur not using your seperate Elastic Cluster and Minio Cluster]

24 GB RAM for the individual swarm nodes (recommended) - for a non Elastic && Minio Cluster env

I will be using a .env file to populate the environment variables for my docker-compose deployment and use constraints to make sure the storage resources do not change on a reboot. (very important) or else you have a high chance of loosing data on reboot.

12 CPU per nodes.

If you are using portainer you can copy paste the docker-compose file and deploy stack. makes your are to initialize the environment variables.

Change the following in your .env file and the docker-compose.yml file
- <API_KEY>
- changeme
- CONNECTOR_ID

It's recommended to change the CONNECTOR_ID.
use https://www.uuidgenerator.net/ to generate the UUIDs.
