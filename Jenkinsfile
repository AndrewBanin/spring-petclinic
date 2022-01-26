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
                sh " jar cvfm classes.jar mymanifest -C foo/ .{spring-petclinic-2.3.1.BUILD-SNAPSHOT.zip}{spring-petclinic}" 
                archiveArtifacts artifacts: 'target/*.jar', followSymlinks: false
            }
        }
    }
}