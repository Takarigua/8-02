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
                    // URL репозитория Nexus
                    def nexusUrl = 'http://localhost:8081/repository/go-binaries/'
                    def fileName = 'myapp'
                    
                    // Загрузка файла на сервер Nexus с использованием анонимного доступа
                    sh "curl -v --upload-file ${fileName} ${nexusUrl}${fileName}"
                }
            }
        }
    }
}
