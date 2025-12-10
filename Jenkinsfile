pipeline {
    agent any
    tools {
        maven 'HW3'
    }
    stages {
        stage('Build') {
            steps {
                sh 'mvn -f initial/pom.xml clean install'
            }
        }
        stage('Save Artifact') {
            steps {
                archiveArtifacts artifacts: 'initial/target/*.jar', fingerprint: true
            }
        }
        stage('Notification'){
            steps{
                telegramSend text: 'Hello', chatId: '-5050415058'
            }
        }
    }
}
