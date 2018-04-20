pipeline {
    agent any
    tools {
        localJDK 'jdk8'
        localMaven 'Maven 3.5.2'
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