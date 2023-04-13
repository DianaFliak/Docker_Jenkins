pipeline {
    agent any
    stages {
        stage('Docker version') {
            steps {
                sh '''
                    echo $USER
                    sudo docker version
                '''
            }
        }
        stage('Build docker image') {
            steps {
                sh '''
                    sudo docker build -t dianafliak/laba:latest .
                '''
            }
        }
        stage('Push docker image to DockerHub') {
            steps{
                withDockerRegistry(credentialsId: 'DockerHub', url: 'https://index.docker.io/v1/') {
                    sh '''
                        sudo docker push dianafliak/laba:latest
                    '''
                }
            }
        }
        stage('Docker delete local image') {
            steps {
                sh '''
                    sudo docker rmi dianafliak/laba:latest
                '''
            }
        }
    }

}
