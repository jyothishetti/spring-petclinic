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
        stage('sonar scanner'){
            steps{
                withSonarQubeEnv ('sonar'){
                    sh 'mvn clean package sonar:sonar'
                }
            }
        }stage(
            steps{
                rtMavenDeployer{
                    id: 'jfrog',
                    serverid: 'artifactory-server-id',
                    releaseRepo: 'joo-libs-libs-release-local',
                    snapshotRepo: 'joo-libs-libs-snapshot-local'
                }

            }
        )
        
        
        

    }
}

