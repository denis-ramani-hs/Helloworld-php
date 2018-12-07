pipeline {
    agent any
    stages {
        stage('build') {
            steps {
                sh 'echo "Hello World"'
                sh 'cat /etc/os-release'
                sh 'mkdir /get-docker'
                sh 'cd /get-docker'
                sh 'curl -fsSL https://get.docker.com -o get-docker.sh'
                sh 'get-docker.sh'
                sh 'docker -v'
            }
        }
    }
}
