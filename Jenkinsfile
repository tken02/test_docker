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
		bat "docker build --tag test:latest ."
                bat "docker tag test:latest tken02/jenkins-docker:latest"
            }
        }
        stage ("Publish to Docker Hub") {
            steps {
                withDockerRegistry(credentialsId: 'docker-hub', url: ''){
                    sh 'docker push tken02/jenkins-docker:latest'
            }
        }
        }
    }

    post {
		always {
			bat 'docker logout'
		}
	}

}
