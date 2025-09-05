pipeline {
    agent any // Specifies that the pipeline can run on any available agent

    stages {
        stage('Checkout Code') {
            steps {
                script {
                    // Checkout a specific branch from a GitHub repository
                    git branch: 'main', // Replace 'main' with your desired branch name
                        credentialsId: 'sachdath@gmail.com', // Replace with the ID of your Jenkins credentials for GitHub
                        url: 'https://github.com/sachdath5/demo-html.git' // Replace with your GitHub repository URL
                }
            }
        }
        // Add more stages for building, testing, or deploying as needed
        stage('Build') {
            steps {
                sh 'sudo cp index.html /var/www/html/index.html' // Example build step (copy File)
                sh 'sudo service nginx reload'
            }
        }
    }

    post {
        always {
            echo 'Pipeline finished.'
        }
        success {
            echo 'Pipeline completed successfully.'
        }
        failure {
            echo 'Pipeline failed.'
        }
    }
}
