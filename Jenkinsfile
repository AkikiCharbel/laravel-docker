pipeline {
    agent any
    environment{
        staging_server="ec2-54-157-141-230.compute-1.amazonaws.com"
    }

    stages {
        stage('Deploy to remote') {
            steps {
                sshagent(credentials: ['final-project']) {
                    sh "scp -v -o StrictHostKeyChecking=no ${WORKSPACE}/* ubuntu@${staging_server}:~/Projects/laravel-docker/"
                }
            }
        }
    }

    post {
        always {
            sshagent(credentials: ['final-project']) {
                sh "ssh ubuntu@${staging_server} 'cd ~/Projects/laravel-docker && docker-compose up -d'"
            }
        }
    }
}
