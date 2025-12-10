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
        stage('Prepare Artifact') {
            steps {
                sh '''
                mkdir -p temp_artifacts
                cp initial/target/*.jar temp_artifacts/
                for f in temp_artifacts/*.jar; do
                    mv "$f" "${f%.jar}-DeclarativePipeline.jar"
                done
                '''
            }
        }

        stage('Push to Other Repo') {
            steps {
                sh """
                if [ ! -d "$TARGET_REPO" ]; then
                    git clone $GIT_URL $TARGET_REPO
                fi

                cp temp_artifacts/*.jar $TARGET_REPO/
                cd $TARGET_REPO
                git add *.jar
                git commit -m "Add DeclarativePipeline artifact from main project"
                git push
                """
            }
        }
    }

    post {
        success { echo 'Artifact pushed successfully!' }
        failure { echo 'Something went wrong.' }
    }
}
        }
    }
}
