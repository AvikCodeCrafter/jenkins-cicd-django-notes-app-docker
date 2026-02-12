pipeline {
    agent {
        label 'akbagent'
    }

    stages {

        stage('Code') {
            steps {
                echo "Cloning the Code"
                git branch: 'main',
                    credentialsId: 'AvikCodeCrafter',
                    url: 'https://github.com/AvikCodeCrafter/jenkins-cicd-django-notes-app-docker.git'
            }
        }

        stage('Build') {
            steps {
                echo "Building Docker Image"
                sh '''
                docker build -t notes-app:latest .
                '''
            }
        }

         stage('Push to Docker Hub') {
            steps {
                echo 'Pushing the Image to Docker Hub'
                withCredentials([usernamePassword(credentialsId: "dockerhub",passwordVariable: "dockerhubpass",usernameVariable: "dockerhubuser")]){
                sh "docker tag django-notes-app ${env.dockerhubuser}/django-notes-app:latest"    
                sh "docker login -u ${env.dockerhubuser} -p ${env.dockerhubpass}"
                sh "docker push ${env.dockerhubuser}/django-notes-app:latest"
                }
            }
        }

        stage('Setup Docker Network') {
            steps {
                echo "Creating Docker Network if not exists"
                sh '''
                docker network inspect notes-network >/dev/null 2>&1 || \
                docker network create notes-network
                '''
            }
        }

        stage('Clean Old Containers') {
            steps {
                echo "Removing old containers if they exist"
                sh '''
                docker rm -f mysql-db || true
                docker rm -f django-notes || true
                '''
            }
        }

        stage('Run MySQL Container') {
            steps {
                echo "Starting MySQL"
                sh '''
                docker run -d \
                --name mysql-db \
                --network notes-network \
                -e MYSQL_ROOT_PASSWORD=rootpass \
                -e MYSQL_DATABASE=notesdb \
                -e MYSQL_USER=notesuser \
                -e MYSQL_PASSWORD=notespwd \
                mysql:8
                '''
            }
        }

        stage('Wait for MySQL') {
            steps {
                echo "Waiting for MySQL to be ready"
                sh '''
                sleep 30
                '''
            }
        }

        stage('Deploy Django App') {
            steps {
                echo "Starting Django Application"
                sh '''
                docker run -d \
                --name django-notes \
                --network notes-network \
                -p 8000:8000 \
                -e DB_NAME=notesdb \
                -e DB_USER=notesuser \
                -e DB_PASSWORD=notespwd \
                -e DB_HOST=mysql-db \
                -e DB_PORT=3306 \
                notes-app:latest
                '''
            }
        }
    }
}
