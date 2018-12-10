pipeline {
    environment {
                DOCKER_USERNAME = credentials('DOCKER_USERNAME_ENV')
                DOCKER_PASSWORD = credentials('DOCKER_PASSWORD_ENV')
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
                    docker rm -f $(docker ps -q -f name=webserver-01)
                    docker run  -d --restart unless-stopped -p 80:80 --name webserver-01 denishs/helloworld-php:1.1
                   '''
            }
        }
    }
    post {
        always {
            sh '''
                docker rmi $(docker images | grep "none" | awk '/ / { print $3 }')
               '''
        }
    }
}
