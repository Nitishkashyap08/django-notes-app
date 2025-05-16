pipeline {
    agent 
        { label 'agent-server' }
    

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
               sh  "docker-compose up -d"
            }
        }
    }
}
