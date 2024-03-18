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
