pipeline{
    agent any
    environment{
        staging_server="52.86.91.204"
    }

    stages{
        stage('Deploy to remote'){
            steps{
                sh 'scp -v -o StrictHostKeyChecking=no ${WORKSPACE}/* root@${staging_server}:/Projects/laravel-docker/'
            }
        }
    }
}
