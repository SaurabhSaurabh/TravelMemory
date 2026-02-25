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
                        echo "Building backend image."
                        sh 'docker build -t backend ./backend'

                        echo "Building frontend image."
                        sh 'docker build -t frontend ./frontend'
                }
        }
        
        stage("Push docker image to dockerhub") {
                    steps {    
                            withCredentials([usernamePassword(credentialsId: 'dockerprogrammer',
                                          usernameVariable: 'DOCKER_USER',
                                          passwordVariable: 'DOCKER_PASS')]) {
                                sh 'echo $DOCKER_PASS | docker login -u $DOCKER_USER --password-stdin'
                    
                                sh 'docker image tag backend:latest dockerprogrammer/travelmemory:backend-jenkins'
                                sh 'docker image tag frontend:latest dockerprogrammer/travelmemory:frontend-jenkins'
                    
                                sh 'docker push dockerprogrammer/travelmemory:backend-jenkins'
                                sh 'docker push dockerprogrammer/travelmemory:frontend-jenkins'
                            }
          }
      }
  }


