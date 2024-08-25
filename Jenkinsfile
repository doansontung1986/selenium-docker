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
            steps {
                sh "docker push doansontung/selenium"
            }
        }
    }

    post {
        always {
            sh "docker system prune -f"
        }
    }
}