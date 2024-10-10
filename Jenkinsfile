pipeline {
    agent any
    
    stages {
        stage('Clone') {
            steps {
                git 'https://github.com/Takarigua/8-02.git'
            }
        }
        stage('Test') {
            steps {
                // Запуск тестов
                sh 'go test ./...'
            }
        }
        stage('Build') {
            steps {
                // Сборка Docker образа
                sh 'docker build . -t ubuntu-bionic:8082/hello-world:v${BUILD_NUMBER}'
            }
        }
        stage('Push') {
            steps {
                // Отправка образа в реестр
                sh 'docker push ubuntu-bionic:8082/hello-world:v${BUILD_NUMBER}'
            }
        }
    }
}
