pipeline {
    environment {
                DOCKER_USERNAME = "denishs"
                DOCKER_PASSWORD = 'Denis@1026'
     }
    agent any    
    stages {
        stage('Build') {
            steps {
                
                sh '''
                    docker -v
                    docker build -t denishs/helloworld-php:1.1 .
                    echo "$DOCKER_PASSWORD" | docker login -u "$DOCKER_USERNAME" --password-stdin
                    docker push denishs/helloworld-php:1.1
                   '''
            }
        }
    }
}
