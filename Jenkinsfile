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
                sh 'mkdir spring-petclinic'
                sh 'cp -r target/*jar spring-petclinic'
                script{
                    zip zipFile: 'spring-petclinic.zip', archive: false, dir: 'spring-petclinic'
                }
               
            }
            steps{
                 archiveArtifacts artifacts: 'spring-petclinic.zip', fingerprint: true
                //archiveArtifacts artifacts: 'target/*.jar', followSymlinks: false
            }
        }
    }
}