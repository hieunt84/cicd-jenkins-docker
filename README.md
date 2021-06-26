# cicd-jenkins-docker
### Object
    setup cicd with jenkins and docker
      - stage: build image with docker
      - stage: push image on docker-hub
      - stage: deploy myapp on localhost using docker

### Step 1 : Set up Env
    - create Vagrantfile
    - creat script setup.sh to deploy git, docker, jenkins 
      admin jenkins: admin/admin

### Step 2: Setup plugin jenkins
    - suggested plugin
    - docker pipeline plugin
    - Kubernetes Continuous Deploy plugin


### Step 3: Create pipeline job on jenkins
    - Config Credentials for docker-hub with name docker-hub
    - Create Jenkinsfile

### Step 4: Run job
    - Check log each stage.
    - Troubeshooting if need.

### Step 5: Enjoy !!!
    curl http://localhost

### Notes
    Chỉ chạy được 1 lần
    Lần sau chạy bi xung đột cần code lại

