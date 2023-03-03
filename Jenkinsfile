pipeline {
    agent any
    environment{
        staging_server="52.86.91.204"
    }

    stages {
        stage('Deploy to remote') {
            steps {
                sshagent(['aws-lab-2']) {
                    sh "scp -v -o StrictHostKeyChecking=no ${WORKSPACE}/* root@${staging_server}:/Projects/laravel-docker/"
                }
            }
        }
    }

    post {
        always {
            sshagent(['aws-lab-2']) {
                sh "ssh root@${staging_server} 'cd /Projects/laravel-docker && docker-compose up -d'"
            }
        }
    }
}
