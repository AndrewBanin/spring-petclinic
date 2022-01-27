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
        stage('Ziping build artifacts') {
            steps {
                sh 'mkdir petclinic'
                sh 'cp -r target/*jar petclinic'
                script{
                    zip zipFile: 'spring-petclinic.zip', archive: false, dir: 'petclinic'
                }
            }
        }
        stage('publishing build artifact'){
            steps{
                 archiveArtifacts artifacts: 'spring-petclinic.zip', fingerprint: true
                //archiveArtifacts artifacts: 'target/*.jar', followSymlinks: false
            }
        }
    }
}