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
                     echo "Logging in to Docker Hub"
                     sh 'echo "dckr_pat__lG3j_LRSAv0-XTM0_ZtNIW2XvY" | docker login -u dockerprogrammer --password-stdin'

                    echo "Tagging backend image"
                    sh 'docker image tag backend:latest dockerprogrammer/travelmemory:backend-jenkins'

                    echo "Tagging frontend image"
                    sh 'docker image tag frontend:latest dockerprogrammer/travelmemory:frontend-jenkins'

                    echo "Pushing backend image"
                    sh 'docker push dockerprogrammer/travelmemory:backend-jenkins'

                    echo "Pushing frontend image"
                    sh 'docker push dockerprogrammer/travelmemory:frontend-jenkins'
   
                }
          }
      }
  }


