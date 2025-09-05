pipeline {
agent any
stages {
stage('Checkout') {
steps {
git 'https://github.com/sachdath5/demo-html.git'
}
}
stage('Deploy') {
steps {
sh '''
sudo cp index.html /var/www/html/index.html
sudo systemctl restart apache2
'''
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
}  
