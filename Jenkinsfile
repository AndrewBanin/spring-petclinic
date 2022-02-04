pipeline{
    agent any
    tools {
      maven 'Maven'
    }
    environment {
		DOCKERHUB_CREDENTIALS=credentials('docker-jenkins-connect')
	}
    stages{
        stage('Maven Build'){
            steps{
                sh "mvn clean package"
            }
            
        }

		stage('Build') {

			steps {
				sh 'docker build -t banina/spring-clinic:latest .'
			}
		}

		stage('Login') {

			steps {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}

		stage('Push') {

			steps {
				sh 'docker push  banina/spring-clinic:latest'
			}
		}
	}

	post {
		always {
			sh 'docker logout'
		}
	}

}