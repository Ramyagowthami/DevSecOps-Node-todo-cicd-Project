pipeline {
    agent any
    environment{
        SONAR_HOME = tool "Sonar"
    }
    
    
    stages {
        
        stage("code"){
            steps{
                git url: "https://github.com/Ramyagowthami/cicd/", branch: "master"
                echo 'code cloned'
            }
        }
        stage("SonarQube Analysis"){
            steps{
               withSonarQubeEnv("testSonarqube"){
                   sh "$SONAR_HOME/bin/sonar-scanner -Dsonar.projectName=nodetodo -Dsonar.projectKey=nodetodo -X"
               }
            }
        }
        stage("SonarQube Quality Gates"){
            steps{
               timeout(time: 1, unit: "MINUTES"){
                   waitForQualityGate abortPipeline: false
               }
            }
        }
    }
}
