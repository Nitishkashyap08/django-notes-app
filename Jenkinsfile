pipeline {
    agent any

    stages {
        stage('clone-stage') {
            steps {
                git url: "https://github.com/Nitishkashyap08/django-notes-app.git", branch: "main"
                echo "git cloned successfully"
            }
        }

        stage('generate-image') {
            steps {
                sh 'docker build -t notes-app:latest .'
                echo "test stage"
            }
        }

        stage('deploy') {
            steps {
                echo "deployed successfully"
               sh  "docker run -d -p 8000:8000 notes-app:latest"
            }
        }
    }
}
