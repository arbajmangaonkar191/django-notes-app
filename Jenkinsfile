@Library("Shared") _

pipeline {
    agent {
        label 'Agent1'
    }

    stages {

        stage('Hello') {
            steps {
                script {
                    hello()
                }
            }
        }

        stage('Code') {
            steps {
                script {
                    clone(
                        "https://github.com/arbajmangaonkar191/django-notes-app.git",
                        "main"
                    )
                }
            }
        }

        stage('Build') {
            steps {
               script{ 
                   build()
               }
            }
        }

        stage('Push on Docker Hub') {
            steps {
                script {
                    push(
                        "Docker-hub",
                        "django_app:latest"
                    )
                }
            }
        }

        stage('Deploy') {
            steps {
               sh 'docker compose up -d'
            }
        }
    }
}
