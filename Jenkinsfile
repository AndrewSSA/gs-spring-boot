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
        stage('Artifacts') {
            steps {
                archiveArtifacts artifacts: initial/target/\*.jar
                }
        }
    }
}
                
            
        


