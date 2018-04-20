pipeline {
    agent any
    tools {
        jdk 'jdk8'
        maven 'Maven 3.5.2'
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