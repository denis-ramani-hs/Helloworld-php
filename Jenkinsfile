pipeline {
    agent any
    stages {
        stage('build') {
            steps {
                sh 'echo "Hello World"'
                sh 'cat /etc/os-release'
                sh 'curl -fsSL https://get.docker.com -o get-docker.sh'
                sh 'sh get-docker.sh'
                sh '''
                   docker -v
                   docker build -t denishs/helloworld-php:1.1 .
                   docker push denishs/helloworld-php:1.1
                   '''
            }
        }
    }
}
