pipeline {
    agent any

    stages {
        stage('Pull the code from github') {
            steps {
                echo "pull master brnach code"
                git url:'https://github.com/SaurabhSaurabh/TravelMemory.git', branch:'main'
            }
        }
    }
}
