   pipeline {
       agent any

       stages {
           stage('Build') {
               steps {
                   script {
                       // Компиляция проекта Go
                       sh 'go build -o myapp main.go'
                   }
               }
           }
           stage('Upload to Nexus') {
               steps {
                   script {
                       // Загрузка артефакта в Nexus
                       def nexusUrl = 'http://localhost:8081/repository/go-binaries/'
                       def fileName = 'myapp'
                       def credentialsId = 'nexus-credentials' // ID учетных данных в Jenkins
                       
                       // Загрузка файла на сервер Nexus
                       sh "curl -v -u admin:admin123 --upload-file ${fileName} ${nexusUrl}${fileName}"
                   }
               }
           }
       }
   }
   

   
