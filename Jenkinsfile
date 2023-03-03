pipeline{
    agent any
    environment{
        staging_server="52.86.91.204"
        ssh_credentials = credentials('aws-2-lab')
    }

    stages{
        stage('Deploy to remote'){
            steps {
                withCredentials([sshUserPrivateKey(credentialsId: ssh_credentials, keyFileVariable: 'SSH_KEY')]) {
                    sh "scp -i $SSH_KEY -o StrictHostKeyChecking=no ${WORKSPACE}/* root@${staging_server}:/Projects/laravel-docker/"
                }
            }
        }
    }
}
