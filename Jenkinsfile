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

        stage("Deploy DEV"){
            steps {
                script {
                  sh """  
                   scp -i tomcat-key.pem target/myapp.war \
                   -o StrictHostKeyChecking=no \
                   ubuntu@ec2-13-127-240-83.ap-south-1.compute.amazonaws.com:/opt/tomcat/webapps

                  """
                }
            }
        }

    }
    post {
        always {
             cleanWs()
        }
    }
}

