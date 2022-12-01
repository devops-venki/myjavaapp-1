pipeline {

    agent any

    stages {

        stage("Build Code"){
            steps {
                cleanWs()
                script {

                    sh """
                    mvn install
                    mv target/*.war target/myapp.war
                    ls -lrt target/*
                    """
                }
            }
        }

        stage("Run Unit Tests"){
            steps {
                script {

                    sh "mvn test"
                }
            }
        }
        stage("Code Analysis"){
            steps {
                echo "Code Analysis....."
            }
        }

        stage("Push Artifacts"){
            steps {
                echo "Uploading Artifacts..."
            }
        }
    }
}