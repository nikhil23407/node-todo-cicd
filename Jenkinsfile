@Library('Shared') _ // Load the Shared library

pipeline {
    agent { label 'slave-1' }

    stages {
        
        stage("Code Clone") {
            steps {
                script{
                clone("https://github.com/nikhil23407/node-todo-cicd.git","master")
                }
            }
        }

        stage("Build") {
            steps {
                script {
                docker_build("node-todo-cicd", "latest", "nikhil23407")
                }
            }
        }

        stage("Push To DockerHub") {
            steps {
                script {
                    docker_push("node-todo-cicd", "latest", "nikhil23407")
                }
            }
        }

        stage("Deploy") {
            steps {
                sh "docker-compose up -d"
            }
        }
    }
}    
