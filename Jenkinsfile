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

        stage('Deploy to QA') {
            steps {
                build job: 'deploy-to-qa'
            }
        }

        stage('Deploy to Production') {
            steps {
                timeout(time:5, 'DAYS'){
                    input message: 'Approve Production Deployment?'
                }

                build job: 'deploy-to-production'                
            }
            post {
                success {
                    echo 'Code deployed to production'
                }

                failure {
                    echo 'Deployment failed'
                }
            }
        }
    }

}