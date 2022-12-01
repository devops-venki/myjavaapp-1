pipeline {

    agent any

    stages {

        stage("Build Code"){
            steps {
                script {

                    sh "mvn install"
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
    }
}