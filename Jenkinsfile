pipeline {

    agent any

    stages {

        stage("Build Code"){
            steps {
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
    }
}