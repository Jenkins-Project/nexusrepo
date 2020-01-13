
pipeline {
   agent { label 'dev' }
   stages {
       stage (checkout){
           steps {
            checkout([$class: 'GitSCM', 
    branches: [[name: '*/master']], 
    userRemoteConfigs: [[credentialsId: 'f1ac5d33-39cc-4531-b485-79bf53848d10', url: 'https://github.com/Jenkins-Project/nexusrepo.git']]
])   
                        }
       }
