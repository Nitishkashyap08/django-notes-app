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

    stage('deploytodockerhun'){
        steps{
            echo "push to dockerhub"
            withCredentials([usernamePassword('CredintialsId':"dockerHubCred",passwordVariable:"dockerHubPass",usernameVariable:"dockerHubUser")]){
                sh "docker login -u ${env.dockerHubUser} -p ${env.dockerHubPass}" 
                sh "docker image tag notes-app:latest ${env.dockerHubUser}/notes-app:latest"
                sh "docker ${env.dockerHubUser}/push notes-app:latest"
            }
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
