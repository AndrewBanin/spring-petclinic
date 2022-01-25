pipeline{
    agent any
    tools {
      maven 'Maven'
    }
    
    stages{
        stage('CONTINOUSDOWNLOAD'){
            steps{
                git credentialsId: 'Github_Token', 
                    url: 'https://github.com/AndrewBanin/spring-petclinic.git'
            }
            
        }
        
        stage('Maven Build'){
            steps{
                sh "mvn clean package"
            }
        }
        stage('Building Jar'){
            steps{
                sh "spring-petclinic-2.3.1.BUILD-SNAPSHOT.jar"
            }
        }

    }
}