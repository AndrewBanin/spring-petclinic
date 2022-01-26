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
                sh "SNAPSHOT.zip", archive: true, dir: 'archive'
                archiveArtifacts artifacts: 'target/*.jar', followSymlinks: false
            }
        }
    }
}