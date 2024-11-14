pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
              docker.image('maven:3.8.7-openjdk-18-slim')
                echo 'Building...'
                command line 'mvn clean && mvn build'
            }
        }
    }
}
