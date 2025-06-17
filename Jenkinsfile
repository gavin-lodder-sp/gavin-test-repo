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
        stage('detect new functions'){
            steps{
                script{

                }
            }
        }
        stage('Documentation Enforcement') {
            steps {
                script {
                    // Helpful documentation: https://plugins.jenkins.io/git/
                    // https://stackoverflow.com/questions/2221658/what-is-the-difference-between-head-and-head-in-git

                    // Get previous git commit
                    def prev = env.GIT_PREVIOUS_SUCCESSFUL_COMMIT ?: sh(
                        script: 'git rev-parse HEAD~1',
                        returnStdout: true
                    ).trim()

                    // Get the number of lines added, deleted, and the file name
                    def diff = sh(
                        script: "git diff --numstat ${prev} HEAD",
                        returnStdout: true
                    ).trim()

                    int linesChanged = 0
                    boolean docsChanged = false

                    echo diff

                    if(codeChanged && !docsChanged){
                        githubPrComment(
                            comment: """
                            !Warning! : A code change has been detected, please update your documentation before merging!
                            """context: 'Docs Checker'
                        )
                    }

                }
            }
        }
        
    
    }
}
