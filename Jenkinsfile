@Library("sharedLib") _
pipeline {
    agent {label 'agent1'}
    stages {
        stage ("Code") {
            steps {
              script{
                  code('https://github.com/afzalhaider1/django-notes-app.git', 'main')
              }
            }
        }
        stage ("Build") {
            steps {
                script{
                    build('afzalhaider1', 'notes-app', 'latest')
                }
            }
        }
        stage ("Push to DockerHub") {
            steps {
                script{
                    docker_push('notes-app', 'latest')
                }
            }
        }
        stage ("Deploy") {
            steps {
                script{
                    docker_compose()
                }
            }
        }
    }
}
