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
    }
}
hi
