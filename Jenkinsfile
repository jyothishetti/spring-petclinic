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
        }
        stage('jfroh pushing'){
            steps{
                rtMavenDeployer (
                    id: 'MAVEN_DEPLOYER',
                    serverid: 'jfrog',
                    releaseRepo: 'joo-lib-libs-release-local',
                    snapshotRepo: 'joo-lib-libs-snapshot-local'
                )
            }
        }

        stage ('Exec Maven') {
            steps {
                rtMavenRun (
                    tool: MAVEN, // Tool name from Jenkins configuration
                    pom: 'pom.xml',
                    goals: 'clean install',
                    deployerId: "MAVEN_DEPLOYER"
                )
            }
        }


            
        
        
        
        

    }
}

