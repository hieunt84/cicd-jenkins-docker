### Commnad
    docker run  -v /var/run/docker.sock:/var/run/docker.sock \
    
                -v $(which docker):$(which docker) \
    
                --privileged \
    
                -v $SH/$WORK_DIR:/var/jenkins_home  \
    
                -p $PORT:8080  \
    
                --user 0:0 \
    
                --name $C_NAME \
    
                -d $IMAGE 
    
    docker run --privileged -p 80:80 --name myapp -d nginx