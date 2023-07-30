pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Checkout the code from your Git repository
                git url: 'https://github.com/Godfrey22152/Jenkins_Angular-Application.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                // Install Node.js dependencies
                sh 'npm install'
            }
        }

        stage('Run Tests') {
            steps {
                // Run unit tests using the Angular CLI
                sh 'npm run test'
            }
        }

        stage('Build') {
            steps {
                // Build the Angular app for production
                sh 'npm run build -- --prod'
            }
        }

        stage('Deploy') {
            steps {
                // Assuming you have SSH access to the remote server
                // Replace 'your_remote_server' with the actual server address
                // Replace '/path/to/deploy' with the target directory on the remote server where you want to deploy the app
                // Make sure the destination directory exists on the remote server

                // Use 'rsync' to copy the build files to the remote server
                sh "rsync -avz --delete./dist/Godfrey22152@your_remote_server:README.md"
            }
        }
    }

    post {
        always {
            // Clean up any temporary files or artifacts after the build and deployment
            deleteDir()
        }

        success {
            echo 'Build and deployment successful!'
        }

        failure {
            echo 'Build or deployment failed. Please check the logs for more details.'
        }
    }
}
