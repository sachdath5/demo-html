pipeline {
agent any
stages {
stage('Checkout') {
steps {
git 'https://github.com/your-repo.git'
}
}
stage('Deploy') {
steps {
sh '''
sudo cp index.html /var/www/html/index.html
sudo systemctl restart nginx
'''
}
}
}
}
