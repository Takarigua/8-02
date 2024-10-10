pipeline {
    agent any

    stages {
        stage('Checkout') {
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
                sh 'docker build -t ubuntu-bionic:8082/hello-world:$BUILD_NUMBER .'
            }
        }
        
        stage('Push') {
            steps {
                script {
                    docker.withRegistry('http://ubuntu-bionic:8082', 'your-credentials-id') {
                        sh "docker push ubuntu-bionic:8082/hello-world:$BUILD_NUMBER"
                    }
                }
            }
        }
    }
}
