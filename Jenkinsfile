pipeline{
    agent any
    tools {
      maven 'Maven'
    }
    }
     stages   
        stage('Maven Build'){
            steps{
                sh "mvn clean package"
            }
        }
        stage('archive artifact'){
            steps{
                archiveArtifacts artifacts: 'target/*.jar', followSymlinks: false 
            }
        }

    }
}