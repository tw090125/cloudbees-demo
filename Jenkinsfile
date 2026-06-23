pipeline {
    agent {
        kubernetes {
            yaml '''
apiVersion: v1
kind: Pod
spec:
  containers:
  - name: shell
    image: alpine:latest
    command:
    - cat
    tty: true
'''
        }
    }

    stages {
        stage('Checkout') {
            steps {
                echo 'Checking out source code from GitHub...'
                checkout scm
            }
        }

        stage('Build') {
            steps {
                container('shell') {
                    sh 'echo "Running build stage..."'
                    sh 'ls -la'
                }
            }
        }

        stage('Test') {
            steps {
                container('shell') {
                    sh './app/hello.sh'
                }
            }
        }

        stage('Deploy') {
            steps {
                container('shell') {
                    sh 'echo "Simulated deployment successful."'
                }
            }
        }
    }
}
