pipeline{
    agent any
    environment{
        staging_server="52.86.91.204"
    }

    stages{
        stage('Deploy to remote'){
            steps{
                sh 'scp ${WORKSPACE}/* root@${staging_server}:/Projects/laravel-docker/'
            }
        }
    }
}
