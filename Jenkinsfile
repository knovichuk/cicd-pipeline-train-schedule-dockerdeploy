pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'docker_hub', usernameVariable: 'username')]) {
                    script {
                        echo 'Running build automation'
                        sh "docker build -t $username/test-train-schedule ."
                    }
                }
            }
        }
        stage('Push to Docker Hub') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'docker_hub', passwordVariable: 'password', usernameVariable: 'username')]) {
                    script {
                        sh "docker login -u $username -p $password"
                        sh "docker push $username/test-train-schedule"
                    }
                }
            }
        }
    }
}