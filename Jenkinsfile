pipeline{
    agent any

    stages{
        stage{'Hello'}{
            steps{
                sh 'python3 helloworld.py'
            }
        }
        stage{'Compute'}{
            steps{
                sh 'python3 compute.py'
            }
        }
        stage{'Version'}{
            steps{
                sh 'python3 --version'
            }
        }
    }
}