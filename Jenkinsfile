pipeline {
    agent any
    environment{
        staging_server="ec2-44-211-125-23.compute-1.amazonaws.com"
    }

    stages {
        stage('Deploy to remote') {
            steps {
                sshagent(credentials: ['final-project']) {
                    sh "scp -v -o StrictHostKeyChecking=no ${WORKSPACE}/* ec2-user@${staging_server}:/Projects/laravel-docker/"
                }
            }
        }
    }

    post {
        always {
            sshagent(credentials: ['final-project']) {
                sh "ssh ec2-user@${staging_server} 'cd /Projects/laravel-docker && docker-compose up -d'"
            }
        }
    }
}
