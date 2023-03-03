pipeline {
    agent any

    stages {
        stage('Deploy to remote') {
            steps {
                sshagent(['jenkins']) {
                    sh "scp -v -o StrictHostKeyChecking=no ${WORKSPACE}/* root@${staging_server}:/Projects/laravel-docker/"
                }
            }
        }
    }

    post {
        always {
            sshagent(['jenkins']) {
                sh "ssh jenkins@${staging_server} 'cd /Projects/laravel-docker && docker-compose up -d'"
            }
        }
    }
}
