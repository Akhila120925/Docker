
pipeline {
    agent any

    stages {

        stage('Build Image') {
            steps {
                echo 'Building Docker Image...'
                bat 'docker build -t registration .'
            }
        }

        stage('Run') {
            steps {
                echo 'Running Docker Container...'
                bat 'docker rm -f reg_app 2>nul || exit /b 0'
                bat 'docker run -d -p 5000:5000 --name reg_app registration'
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully!'
        }

        failure {
            echo 'Pipeline failed. Please check the Jenkins logs.'
        }
    }
}


