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

1.	Forked the repo to my github account in this repo. When trying to deploy the app on docker for testing purpose, had some trouble to solve it made changes to 2 lines in the node.js app code  and deployed the app successfully on docker as a test
2.	Created Minikube Cluster on AWS EC2-Instance using this procedure.
3.	Created a Jenkins namespace and created the pod inside this namespace using these manifests.
4.	Switched context using kubectl config set-context --current --namespace=Jenkins

 
 

5.	Created a multi-branch pipeline with github hook, provided Jenkins file from Github Repo
6.	In first stage of the peipeline code is pulled from github along with dockerfile needed to build it.
7.	In the next stage image is built and pushed into dockerhub repo.
8.	I am currently working on the deployment of the app using kubernetes agent to deploy the app on host machine as of now running into some issues. Will update the documentation as soon as it gets solved.


