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
                archiveArtifacts artifacts: 'BUILD-SNAPSHOT.zip', followSymlinks: false
                archiveArtifacts artifacts: 'target/*.jar', followSymlinks: false
            }
        }
    }
}