pipeline {
    agent any
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
                    docker build -t bohdan004/apteka:latest .
                '''
            }
        }
        stage('Push docker image to DockerHub') {
            steps{
                withDockerRegistry(credentialsId: 'DockerHub', url: 'https://index.docker.io/v1/') {
                    sh '''
                        docker push bohdan004/apteka:latest
                    '''
                }
            }
        }
        stage('Docker delete local image') {
            steps {
                sh '''
                    docker rmi bohdan004/apteka:latest
                '''
            }
        }
    }

}
