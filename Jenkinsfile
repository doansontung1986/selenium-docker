pipeline {

    agent any

    stages {
        stage('Build Jar') {
            steps {
                sh "mvn clean package -DskipTest"
            }
        }

        stage('Build Image') {
            steps {
                sh "docker build -t=doansontung/selenium ."
            }
        }

        stage('Push Image') {
            environment {
                DOCKER_HUB = credentials('dockerhub-creds')
            }

            steps {
                sh 'docker login -u ${DOCKER_HUB_USR} -p ${DOCKER_HUB_PSW}'
                sh "docker push doansontung/selenium"
            }
        }
    }

    post {
        always {
            sh "docker logout"
        }
    }
}