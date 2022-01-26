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
                archiveArtifacts artifacts: 'spring-petclinic-2.3.1.BUILD-SNAPSHOT/*.zip', archive: true, dir: 'archive'
                archiveArtifacts artifacts: 'target/*.jar', followSymlinks: false
            }
        }
    }
}