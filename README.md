## Decentralized Docker Hub

Using Decentralized Docker Hub, you can easily push and pull docker images
from IPFS and filecoin. It is powered by Powergate.


## Getting Started

1) Install Docker and Docker compose
   ```
   https://docs.docker.com/engine/install/#server
   https://docs.docker.com/compose/install/
   ```
      
2) Run Powergate, Lotus and IPFS containers
   
   ```
   git clone https://github.com/textileio/powergate.git
   cd powergate
   make build-pow
   make build-powd
   cd docker
   BIGSECTORS=true make localnet
   ```
      
 3) Create a FFS instance from a new tab and note down the token from the output
 
    ```
    pow ffs create
    ```
    
 4) Add token as the environment variable
 
    ```
    export POWERGATE_TOKEN={token}
    ```
    
    Replace {token} in the above command with the actual token
    
 5) Determine the docker image that you want to push to IPFS and filecoin
 
    You can either create a new docker image locally or fetch it 
    from another source
    
    You can check the list of existing docker images in your local 
    machine using `docker image ls`
    
    For this tutorial lets use `alpine` docker image since it is a 
    lightweight Linux distribution
    
 6) Clone Decentralized Docker Hub repo
 
    ```
    git clone https://github.com/viraja1/decentralized_docker_hub.git
    cd decentralized_docker_hub
    ```
 
 7) Push alpine image to IPFS and filecoin
 
    ```
    ./ddocker push alpine
    ```
    
    Note down the IPFS cid from the output since it will be required
    for the next step
    
 8) Pull alpine image from IPFS and filecoin
 
    ```
    ./ddocker pull {cid}
    ```
    
    Replace {cid} with the IPFS cid noted from the previous step
    
 9) Create a test container
    ```
    docker container run -it -d alpine
    ```
    
    