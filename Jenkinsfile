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
                    docker login -u dockerprogrammer -p dckr_pat__lG3j_LAGSAv0-XT
                    docker image tag backend:latest dockerprogrammer/travelmemory:backend-jenkins:01
                    docker image tag frontend:latest dockerprogrammer/travelmemory:frontend-jenkins:01
                    docker push -u dockerprogrammer/travelmemory:backend-jenkins:01
                    docker push -u dockerprogrammer/travelmemory:frontend-jenkins:01
                }
          }
      }
  }


