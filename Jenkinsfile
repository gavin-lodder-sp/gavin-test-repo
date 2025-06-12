@Library('sailpoint/jenkins-release-utils')_

pipeline {
    agent {
        kubernetes {
            yaml libraryResource("pods/aws-cli-dev.yaml")
        }
    }

    stages {
        stage('stage 1') {
            steps {
                script {
                    println("HELLO WORLD")
                }
            }
        }
        stage('stage 2') {
            steps {
                container('python3') {
                    sh 'python3 compute.py'
                }
            }
        }
    }
}
