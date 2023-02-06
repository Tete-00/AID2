pipeline{

	agent any

	environment {
		DOCKERHUB_CREDENTIALS_USR='tete2023'
		DOCKERHUB_CREDENTIALS_PSW='Teresa123'
	}


	stages {

		stage('Build') {

			steps {
				bat 'docker build -t tete2023/appweb:latest .'
			}
		}

		stage('Login') {

			steps {
				bat 'docker login -u %DOCKERHUB_CREDENTIALS_USR% -p %DOCKERHUB_CREDENTIALS_PSW%'
			}
		}

		stage('Push') {

			steps {
				bat 'docker push tete2023/appweb:latest'
				bat 'docker image prune -a -f'
			}
		}	
	}

	post {
		always {
			bat 'docker logout'
		}
	}

}