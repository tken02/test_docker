pipeline {
    agent any
    stages {
        stage('gitclone') {

			steps {
				git branch: 'main', url: 'https://github.com/tken02/test_docker.git'
			}
		}
        stage ("Build Docker Image and Tag") {
            steps {
                bat 'docker build -t tken02/jenkins-docker:latest .'
            }
        }
        stage ("Publish to Docker Hub") {
            steps {
<<<<<<< HEAD
                withDockerRegistry(credentialsId: 'docker-hub', url:"") {
                    sh 'docker push tken02/jenkins-docker:latest'
=======
                withDockerRegistry(credentialsId: "dockerhub", url: "") {
                    bat 'docker push tken02/jenkins-docker:latest'
>>>>>>> 86594f1cfc726a86926038b07f75e4cd6ec3c315
                }
            }
        }
    }
    post {
		always {
			sh 'docker logout'
		}
	}
}
