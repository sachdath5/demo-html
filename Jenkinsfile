pipeline {
    agent any
    environment {
        BUCKET_NAME = 'demotest1233456764345qwe'
    }
    stages {
        stage('Checkout') {
            steps {
                echo "checkout"
                sh 'aws s3 ls'
                git branch: 'main', url: 'https://github.com/sachdath5/demo-html.git'
            }
        }
        stage('check Bucket') {
            steps {
                echo 'check if bucket is there or not'
                sh '''
                if aws s3 ls s3://$BUCKET_NAME; then
                echo "bucket already exit"
                else
                aws s3 mb s3://$BUCKET_NAME
                fi
                '''
            }
        }
        stage('deploy') {
            steps {
                echo 'sync to s3 bucket'
                sh 'aws s3 sync . s3://${BUCKET_NAME}/'
            }
        }
    }
  post{
      always {
          echo "it will run always"
      }
      failure {
          echo "pipeline got failed"
      }
      success {
          echo "creating the artifact"
          sh 'tar -cvf demo.tar index.html'
      }
  }
}
