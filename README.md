#    
# shlink-docker   
A Docker  Compose implementation of [Shlink](https://shlink.io) with Postgres backend
   
Clone the repo   
```
git clone https://github.com/0daven/shlink-compose
cd shlink-compose
```
copy the .env.sample into .env   
```
cp .env.sample .env
```
We need a GEOLITE API key, which are free, you can learn more [HERE](https://shlink.io/documentation/geolite-license-key/)   
edit .env to update the value   
```
nano .env

POSTGRES_PASSWORD=Ch4ngeme
DEFAULT_DOMAIN=yourdomain.tld
GEOLITE_LICENSE_KEY=license_key
SHLINK_SERVER_URL=https://yourdomain.tld
SHLINK_SERVER_API_KEY=#see readme to generate this key

```
Update the values except SHLINK\_SERVER\_API\_KEY   
```
docker compose up -d
```
Wait some seconds for the dockers to be up and running and run the following command to obtain the value for SHLINK\_SERVER\_API\_KEY   
```
docker exec -it shlink_stable shlink api-key:generate
```
Copy the provided value   
Update .env   
```
nano .env

SHLINK_SERVER_API_KEY= pasteyourkeyhere

```
Redeploy the containers   
```
docker compose up -d --build --force-recreate
```
Shlink API is exposed on port 8081, make use of your favourite proxy to present to the outside.   
