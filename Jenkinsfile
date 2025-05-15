pipeline {
    agent {
        label 'dev-server'
    }

    stages {
        stage('clone-stage') {
            steps {
                git url: "https://github.com/Nitishkashyap08/django-notes-app.git", branch: "main"
                echo "git cloned successfully"
            }
        }

        stage('test') {
            steps {
                echo "test stage"
            }
        }

        stage('deploy') {
            steps {
                echo "deployed successfully"
            }
        }
    }
}
