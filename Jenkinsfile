@Library("shared") _
pipeline {
    agent { label 'agent-server' }

    stages {
        
        stage('clone-stage') {
            steps {
                git url: 'https://github.com/Nitishkashyap08/django-notes-app.git', branch: 'main'
                echo 'Git cloned successfully'
            }
        }

        stage('generate-image') {
            steps {
                sh 'docker build -t notes-app:latest .'
                echo 'Docker image built'
            }
        }

        stage('deploytodockerhub') {
            steps {
                echo 'Pushing to Docker Hub'
                withCredentials([usernamePassword(credentialsId: 'dockerHubCred', passwordVariable: 'dockerHubPass', usernameVariable: 'dockerHubUser')]) {
                    sh 'docker login -u $dockerHubUser -p $dockerHubPass'
                    sh 'docker tag notes-app:latest $dockerHubUser/notes-app:latest'
                    sh 'docker push $dockerHubUser/notes-app:latest'
                }
            }
        }

        stage('deploy') {
            steps {
                echo 'Deploying using docker-compose'
                echo 'testing purpose using web-hook'
                sh '''
                    docker rm -f db_cont || true
                    docker-compose up -d
                '''
            }
        }
    }
}
