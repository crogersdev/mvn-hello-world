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
                    sh '''
                    cd harness-app
                    ls -latrh
                    mvn clean
                    '''
                }
            }
        }
    }
}
