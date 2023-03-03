pipeline {
    agent any
    environment{
        staging_server="52.86.91.204"
    }

    stages {
        stage('Deploy to remote') {
            steps {
                sshagent(credentials: ['aws-lab-2']) {
                    sh "scp -v -o StrictHostKeyChecking=no ${WORKSPACE}/* ubuntu@${staging_server}:/Projects/laravel-docker/"
                }
            }
        }
    }

    post {
        always {
            sshagent(credentials: ['aws-lab-2']) {
                sh "ssh ubuntu@${staging_server} 'cd /Projects/laravel-docker && docker-compose up -d'"
            }
        }
    }
}
