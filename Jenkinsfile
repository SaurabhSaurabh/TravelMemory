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
    }
}
