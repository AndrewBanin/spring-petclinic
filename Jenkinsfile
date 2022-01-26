pipeline{
    agent any
    tools {
      maven 'Maven'
    }
    stages {    
        stage('Maven Build') {
            steps{
                sh "mvn clean package"
            }
        }
        stage('Zip and Publish artifacts') {
            steps {
                archiveArtifacts artifacts: 'spring-petclinic-2.3.1.BUILD-SNAPSHOT.zip.jar', followSymlinks: false
                archiveArtifacts artifacts: 'target/*.jar', followSymlinks: false
            }
        }
    }
