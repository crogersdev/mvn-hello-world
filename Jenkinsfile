pipeline {
    agent {
        kubernetes {
            yaml '''
                apiVersion: v1
                kind: Pod
                spec:
                    containers:
                    - name: maven-foo
                      image: maven:3.8.7-openjdk-18-slim
                      tty: true
                      command: ["cat"]
                 
            '''
        }
    }

    stages {
        stage('Build') {
            steps {
                container('maven-foo') {
                    sh 'mvn -version || echo "i don\'t have that command"'
                    sh 'ls -latrh'
                    sh 'pwd'
                    sh 'cd harness-app'
                    sh 'ls -latrh'
                    sh 'mvn clean || echo "couldnt run mvn clean"'
                    sh 'mvn build || echo "couldnt run mvn build"'
                    sh 'ls -latrh'
                }
            }
        }
    }
}
