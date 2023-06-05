pipeline{
    agent any
    stages{
        stage('cloning the code'){
            steps{
                git branch:'main', url:'https://github.com/jyothishetti/spring-petclinic.git'
            }
        }
        stage('bulid mvn'){
            steps{
                sh 'mvn package'
            }
        }
        stage('archive artifacts'){
            steps{
                archiveArtifacts artifacts: 'target/*.jar'
            }
        }
        stage('testunit'){
            steps{
                junit '**/surefire-reports/*.xml'
            }
        }
        
        
        

    }
}

