pipeline {
    agent { label 'node' }
    stages {
        stage('Docker version') {
            steps {
                sh '''
                    echo $USER
                    docker version
                '''
            }
        }
        stage('Build docker image') {
            steps {
                sh '''
                    docker build -t dianafliak/laba:latest .
                '''
            }
        }
        stage('Push docker image to DockerHub') {
            steps{
                withDockerRegistry(credentialsId: 'Docker', url: 'https://index.docker.io/v1/') {
                    sh '''
                        docker push dianafliak/laba:latest
                    '''
                }
            }
        }
        stage('Docker delete local image') {
            steps {
                sh '''
                    docker rmi dianafliak/laba:latest
                '''
            }
        }
    }

}
