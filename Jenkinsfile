pipeline{
    
    agent any
    stage('gitclone') {

			steps {
				git branch: 'main', url: 'https://github.com/tken02/test_docker.git'
			}
		}
    stages {
        stage ("Build Docker Image and Tag") {
            steps {
                sh 'docker build -t tken02/jenkins-docker:latest .'
                sh "docker tag jenkins-docker:latest tken02/jenkins-docker:latest"
            }
        }
        stage ("Publish to Docker Hub") {
            steps {
                withDockerRegistry(credentialsId: "dockerhub", url: "") {
                    sh 'docker push hungle11/jenkins-docker:latest'
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
