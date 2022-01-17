pipeline {
    agent any
<<<<<<< HEAD
=======

>>>>>>> db6808a6b74911542a708e34af19cb003f3a13f1
    stages {
        stage('gitclone') {

			steps {
				git branch: 'main', url: 'https://github.com/tken02/test_docker.git'
			}
		}
        stage ("Build Docker Image and Tag") {
            steps {
                sh 'docker build -t tken02/jenkins-docker:latest .'
                sh "docker tag enkins-docker:latest tken02/jenkins-docker:latest"
            }
        }
        stage ("Publish to Docker Hub") {
            steps {
                withDockerRegistry(credentialsId: "dockerhub", url: "") {
                    sh 'docker push tken02/jenkins-docker:latest'
                }
            }
        }
    }
    post {
		always {
			sh 'docker logout'
		}
	}
<<<<<<< HEAD
}
=======
}
>>>>>>> db6808a6b74911542a708e34af19cb003f3a13f1
