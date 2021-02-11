# Skupper strest-grpc example

strest-grpc home: https://github.com/BuoyantIO/strest-grpc

## Step 1:
   ```bash
   git clone https://github.com/ajssmith/skupper-example-strest.git
   ```

## Step 2: 
On server site and namespace
   ```bash
   skupper init --site-name server-site
   skupper token create server-site-token.yaml
   ```

## Step 3: 
On client site and namespace
   ```bash
   skupper init --site-name client-site
   skupper link create server-site-token.yaml
   ```

## Step 4: 

On server site, deploy and expose the server

   ```bash
   kubectl apply -f ./server.yaml
   skupper service create strest-server 11111 --mapping http2
   skupper service bind strest-server deployment strest-server
   ```

## Step 5: 

On client site, deploy client

   ```bash
   kubectl apply -f ./client.yaml
   ```

## Step 5: 

On client site, observe client pod log