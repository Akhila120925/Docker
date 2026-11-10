
pipeline {
    agent any

    stages {

        stage('Build') {
            steps {
                echo 'Building Docker Image...'
                bat 'docker build -t sample .'
            }
        }

        stage('Run') {
            steps {
                echo 'Running Docker Container...'

                // Remove old container if it exists
                bat 'docker rm -f week7 2>nul || exit /b 0'

                // Run the new container
                bat 'docker run -d -p 5000:5000 --name week7 sample'
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
