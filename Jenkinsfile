pipeline {
    agent any
    tools {
        jdk 'localJDK'
        maven 'localMaven'
    }
    stages{
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }

            post {
                success {
                    echo 'Now Archiving ...'
                    archiveArtifacts artifacts: "**/target/*.war"
                }
            }
        }
    }

}