pipeline {
    agent any
    tools {
        jdk 'localJDK'
        maven 'localMaven'
    }
    stages {

        stage("Build"){
            steps {
                sh "mvn clean package"
            }
            post{
                always {
                    echo "========always========"
                }
                success {
                    echo "========Build executed successfully========"
                    archiveArtifacts artifacts: "**/target/*.war"
                }
                failure{
                    echo "========A execution failed========"
                }
            }
        }

        stage("Deploy to Staging") {
            steps {
                build job: "AWS-Deploy-to-Staging"
            }
        }
    }
    post{
        always{
            echo "========always========"
        }
        success{
            echo "========pipeline executed successfully ========"
        }
        failure{
            echo "========pipeline execution failed========"
        }
    }
}