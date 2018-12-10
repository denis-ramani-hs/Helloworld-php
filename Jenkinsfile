pipeline {
    agent any    
    stages {
        stage('Build') {
            steps {
                
                sh '''
                    docker -v
                    docker build -t denishs/helloworld-php:1.1 .
                    docker push denishs/helloworld-php:1.1
                   '''
            }
        }
    }
}
