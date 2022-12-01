pipeline {

    agent any
    environment{
        DEV_SERVER="ec2-13-127-240-83.ap-south-1.compute.amazonaws.com"
        UAT_SERVER="ec2-13-234-38-235.ap-south-1.compute.amazonaws.com"
        PROD_SERVER="ec2-13-234-32-64.ap-south-1.compute.amazonaws.com"
    }

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
                   chmod 400 tomcat-key.pem
                   scp -o StrictHostKeyChecking=no \
                   -i tomcat-key.pem target/myapp.war \
                   ubuntu@${DEV_SERVER}:/opt/tomcat/webapps

                  """
                }
            }
        }

        stage("Deploy UAT"){
            steps {
                script {
                  sh """  
                   chmod 400 tomcat-key.pem
                   scp -o StrictHostKeyChecking=no \
                   -i tomcat-key.pem target/myapp.war \
                   ubuntu@${UAT_SERVER}:/opt/tomcat/webapps

                  """
                }
            }
        }

        stage("Deploy PROD"){
             input {
                message "Should we continue?"
                ok "Yes, we should."
            }
            steps {
                script {
                  sh """  
                   chmod 400 tomcat-key.pem
                   scp -o StrictHostKeyChecking=no \
                   -i tomcat-key.pem target/myapp.war \
                   ubuntu@${PROD_SERVER}:/opt/tomcat/webapps

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

