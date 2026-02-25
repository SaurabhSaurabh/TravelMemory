pipeline {
    agent any

    stages {
        stage('Pull the code from github') {
            steps {
                echo "pull master brnach code"
                git url:'https://github.com/SaurabhSaurabh/TravelMemory.git', branch:'main'
            }
        }
        stage("Build docker image") {
                steps {
                        echo "Building backend image"
                        sh 'docker build -t backend ./backend'

                        echo "Building frontend image"
                        sh 'docker build -t frontend ./frontend'
                }
        }
        stage("Push docker image to dockerhub") {
            steps {
                withCredentials([usernamePassword('credentialsId': 'docker',
                usernameVariable: 'dockerHubUser',
                passwordVariable: 'dockerHubPass')]){
                    
                    docker image tag backend:latest pipeline {
    agent any

    stages {
        stage('Pull the code from github') {
            steps {
                echo "pull master brnach code"
                git url:'https://github.com/SaurabhSaurabh/TravelMemory.git', branch:'main'
            }
        }
        stage("Build docker image") {
                steps {
                        echo "Building backend image"
                        sh 'docker build -t backend ./backend'

                        echo "Building frontend image"
                        sh 'docker build -t frontend ./frontend'
                }
        }
        stage("Push docker image to dockerhub") {
            steps {
                withCredentials([usernamePassword('credentialsId': 'docker',
                usernameVariable: 'dockerHubUser',
                passwordVariable: 'dockerHubPass')]){
                    
                    docker image tag backend:latest dockerprogrammer/travelmemory:backend-jenkins:01
                    docker image tag frontend:latest dockerprogrammer/travelmemory:frontend-jenkins:01

                    sh "docker login -u ${env.dockerHubUser} -p ${env.dockerHubPass}"
                    sh "docker push  ${env.dockerHubUser}/travelmemory:backend-jenkins:01"
                    sh "docker push  ${env.dockerHubUser}/travelmemory:frontend-jenkins:01"
                }
            }
        }
    }
}
/travelmemory:backend-jenkins:01
                    docker image tag frontend:latest ${env.dockerHubUser}/travelmemory:frontend-jenkins:01

                    sh "docker login -u ${env.dockerHubUser} -p ${env.dockerHubPass}"
                    sh "docker push  ${env.dockerHubUser}/travelmemory:backend-jenkins:01"
                    sh "docker push  ${env.dockerHubUser}/travelmemory:frontend-jenkins:01"
                }
            }
        }
    }
}
