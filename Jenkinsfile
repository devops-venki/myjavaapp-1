pipeline {
    agent any
    environment {
       REPO_URL="https://github.com/doggadevops/war-web-project"
    }
    stages{
        stage("Build code"){
            steps{
                script{
                    sh """
                    ls -lrt
                    mvn install
                    """
                }
            }
        }
        stage("Run Unit Test"){
            steps{
                script {
                    sh """
                    mvn test
                    """
                }
            }
        }
        stage("Code Analysis"){
            steps{
                echo "Running Code Analysis..."
            }
        }

        stage("Push Artifacts"){
            steps{
                echo "Pushing Artifacts..."
            }
        }
    }
}
