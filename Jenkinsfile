node('linux') {
  stage('Unit Tests') {
    git 'https://github.com/lbutlr093/java-project.git'
    sh 'ant -f test.xml -v'
    junit 'reports/*.xml'
  }
  stage('Build') {
    sh 'ant -f build.xml -v'
  }
  stage('Deploy') {
    withCredentials([[$class: 'AmazonWebServicesCredentialsBinding', accessKeyVariable: 'AWS_ACCESS_KEY_ID', credentialsId: 'cef8ac76-7a74-4b42-8410-c4d38ec24e88', secretKeyVariable: 'AWS_SECRET_ACCESS_KEY']]) {
      sh 'aws cloudformation describe-stack-resources --region us-east-1 --stack-name jenkins'
    }
  }
  stage('Report') {
    withCredentials([[$class: 'AmazonWebServicesCredentialsBinding', accessKeyVariable: 'AWS_ACCESS_KEY_ID', credentialsId: 'cef8ac76-7a74-4b42-8410-c4d38ec24e88', secretKeyVariable: 'AWS_SECRET_ACCESS_KEY']]) {
      sh 'aws cloudformation describe-stack-resources --region us-east-1 --stack-name jenkins'
    }
    junit 'reports/*.xml'
  }
}
