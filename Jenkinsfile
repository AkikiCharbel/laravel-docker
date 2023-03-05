pipeline {
    agent any
    environment{
        staging_server="ec2-54-157-189-39.compute-1.amazonaws.com"
    }

    stages {
        stage('Deploy to remote') {
            steps {
                sshagent(credentials: ['final-project']) {
                    sh "scp -r -v -o StrictHostKeyChecking=no ${WORKSPACE}/* ubuntu@${staging_server}:~/Project/laravel-docker/"
                }
            }
        }
    }

    post {
        always {
            sshagent(credentials: ['final-project']) {
                sh "ssh ubuntu@${staging_server} 'cd ~/Project/laravel-docker && docker compose up -d'"
            }
        }
    }
}
