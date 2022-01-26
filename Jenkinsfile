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
                sh 'mkdir archive'
                sh 'echo target > archive/target.txt'
                zip zipFile: 'target.zip', archive: false, dir: 'archive'
                archiveArtifacts artifacts: 'target.zip', fingerprint: true
                archiveArtifacts artifacts: 'target/*.jar', followSymlinks: false
            }
        }
    }
