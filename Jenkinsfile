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
        stage('Save Artifact&Job end notify') {
            steps {
                archiveArtifacts artifacts: 'initial/target/*.jar', fingerprint: true
                telegramSend(message: 'Hello World', chatId: -5050415058)
            }
        }
    }
}
