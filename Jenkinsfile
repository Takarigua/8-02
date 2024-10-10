   pipeline {
       agent any

       stages {
           stage('Clone') {
               steps {
                   git branch: 'main', url: 'https://github.com/Takarigua/8-02.git'
               }
           }
           stage('Test') {
               steps {
                   sh 'go test ./...'
               }
           }
           stage('Build') {
               steps {
                   sh 'docker build . -t ubuntu-bionic:8082/hello-world:v${BUILD_NUMBER}'
               }
           }
           stage('Push') {
               steps {
                   sh 'docker push ubuntu-bionic:8082/hello-world:v${BUILD_NUMBER}'
               }
           }
       }
   }
   
