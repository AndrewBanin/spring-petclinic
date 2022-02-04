pipeline{
    agent any
    tools {
      maven 'Maven'
    }
    environment {
      DOCKER_TAG = getVersion()
    }
    stages{
        stage('Maven Build'){
            steps{
                sh "mvn clean package"
            }
            
        }
        
        stage('Docker Build'){
            steps{
                sh "docker build . -t banina/spring-clinic:${DOCKER_TAG}"
                
            }
            
        }
        stage('Docker Push'){
            steps{
                sh "docker login -u banina -p password"
                sh "docker push banina/spring-clinic:${DOCKER_TAG}"    
            }
            
        }
    }  
}
def getVersion(){
    def commitHash = sh returnStdout: true, script: 'git rev-parse -- short HEAD'
    return commitHash
 }   