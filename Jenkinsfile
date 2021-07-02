pipeline {
    agent any
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