Cliff.ai Assignment - Documentation
- Akhil Prakash Karvanje
akhilkarvanje@gmail.com
7021404394

Problem Statement: 
1.	Create K8s Cluster in your local system. For this you can use Minkube or K3s
2.	Switch your current context to the newly created cluster’s context using kubeconfig file and deploy the Jenkins server on your namespace and expose Jenkins
3.	Fork this repo to your own git account( GitLab). https://gitlab.com/cliff-public/assignment_app. You will not be able to create a SCM trigger directly using this URL. You will need to fork or clone it to your account in order to proceed.

Deployment:
Setup a multibranch CI/CD Pipeline on Jenkins that will have 3 stages (This pipeline will be triggered automatically when someone pushes to SCM repository) .
1. The code will be pulled from the SCM repository(which you have forked) to Jenkins .
2. The Docker image will be created in the second stage and pushed to a private repository. (you can use your DockerHub repository as it provides one private repository as free trial)
3. In the third stage, The pushed image will be deployed as a deployment with high-availability in k8s cluster.


Approach to the solution:

Tools Used: AWS, Docker, Dockerhub,  Kubernetes, Jenkins.

1.	Forked the repo to my github account in [this](https://github.com/rookie1025/app.git) repo. When trying to deploy the app on docker for testing purpose, had some trouble to solve it made changes to 2 lines in the node.js app code  and deployed the app successfully on docker as a test
2.	Created Minikube Cluster on AWS EC2-Instance using [this](https://github.com/rookie1025/How_to_minikube_aws_ec2_install.git) procedure.
3.	Created a Jenkins namespace and created the pod inside this namespace using [these](https://github.com/rookie1025/Cliff_Assignment_Documentation.git) manifests.
4.	Switched context using kubectl config set-context --current --namespace=Jenkins

![image](https://user-images.githubusercontent.com/22639401/191261224-abde7610-889d-4f67-9e8e-a6f1d4057483.png)
![image](https://user-images.githubusercontent.com/22639401/191261257-bc4b8c58-fba5-440d-ba6d-233a72b947a4.png)

 

5.	Got the Jenkins password from kubectl logs command and logged in to server. Created a multi-branch pipeline with github hook, provided Jenkins file from Github Repo 
6.	In first stage of the peipeline code is pulled from github along with dockerfile needed to build it.
7.	In the next stage image is built and pushed into dockerhub repo.
8.	I am currently working on the deployment of the app using kubernetes agent to deploy the app on host machine as of now running into some issues. Will update the documentation as soon as it gets solved.

Jenkins URL: http://43.205.203.53:31137/ | Username: admin | Password: admin@12345
App deployment done using [this](https://github.com/rookie1025/deployment.git) file. Please note that I am currently trying to resolve issues with automatic deployment. Currently app is deployed manually post build is done.
App URL: http://43.205.203.53:32591/

[KubeConfig](https://github.com/rookie1025/Cliff_Assignment_Documentation/blob/main/kube%20config%20file) File
[JenkinsFIle](https://github.com/rookie1025/app/blob/main/JenkinsFile)

![image](https://user-images.githubusercontent.com/22639401/191565529-41b39083-1cf4-4ba2-9681-0e36c81b7e9f.png)
