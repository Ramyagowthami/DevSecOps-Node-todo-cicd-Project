pipeline {
    agent any
    environment{
        SONAR_HOME = tool "Sonar"
    }
    stages {
        stage("code"){
            steps{
        stage('Build Maven'){
            steps{
                git url:'https://github.com/Ramyagowthami/DevSecOps-Node-todo-cicd-Project/', branch: "master"
               sh 'mvn clean install'
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
