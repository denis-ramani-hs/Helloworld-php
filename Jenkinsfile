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
        stage('Update') {
            steps {
                sh '''
                    docker rm -f $(docker ps -q -f ancestor=denishs/helloworld-php:1.1)
                    docker run  -d --restart unless-stopped -p 80:80 denishs/helloworld-php:1.1
                   '''
            }
        }
    }
}
