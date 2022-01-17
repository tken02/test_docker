pipeline{

	agent any

	environment {
		DOCKERHUB_CREDENTIALS=credentials('docker hub')
	}

	stages { 
	    stage('gitclone') {

			steps {
				git branch: 'main', url: 'https://github.com/tken02/test_docker.git'
			}
		}
		stage('Build') {
			steps {
				withDockerRegistry(credentialsId: 'docker-hub', url:"") {
                    sh 'docker build -t hungle11/jenkins-docker:latest .'
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
