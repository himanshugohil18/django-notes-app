@Library('Shared') _
pipeline {
    agent { label 'vinod' }

    stages {

        stage("Code Clone") {
            steps {
                sh "whoami"
                clone(
                    "https://github.com/himanshugohil18/django-notes-app.git",
                    "main"
                )
            }
        }

        stage("Code Build") {
            steps {
                docker_build(
                    imageName: "notes-app",
                    tag: "latest"
                )
            }
        }

        stage("Push to DockerHub") {
            steps {
                docker_push(
                    imageName: "notes-app",
                    imageTag: "latest",
                    credentials: "dockerHubCred"
                )
            }
        }

        stage("Deploy") {
            steps {
                deploy()
            }
        }
    }
}
