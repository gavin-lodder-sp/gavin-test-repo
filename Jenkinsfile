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
                sh 'python3 helloworld.py'
            }
        }
        stage('Compute'){
            steps{
                sh 'python3 compute.py'
            }
        }
        stage('stage 3'){
            script{
            println("HELLO WORLD")
            }
        }
    }
}
