
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
        stage (build){
           steps {
               sh 'mvn package'
                 }
                         }
        stage (sonar){
           steps {
               sh 'mvn sonar:sonar -Dsonar.host.url=http://15.206.123.54:9000 -Dsonar.credentials=admin:admin'
                 }
                         }    
        stage (nexus){
           steps {
               sh 'mvn -Dv=${BUILD_NUMBER} deploy'
                 }
                         }     
        stage (deploy){
           steps {
               sh 'scp /root/workspace/pipeline/target/*.war 13.234.238.52:/var/lib/tomcat/webapps'
                 }
                         }                    
           }
             }
