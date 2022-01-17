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
                withDockerRegistry(credentialsId: 'docker-hub', url: 'https://index.docker.io/v1/'){
                    bat 'docker push tken02/jenkins-docker:latest'
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
