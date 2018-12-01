node('linux') {
  stage('Unit Tests') {
    git 'https://github.com/lbutlr093/java-project.git'
    sh 'ant -f test.xml -v'
    junit 'reports/*.xml'
  }
  stage('Build') {
    sh 'ant -f build.xml -v'
  }
  stage('Results') {
    withCredentials([[$class: 'AmazonWebServicesCredentialsBinding', accessKeyVariable: 'AWS_ACCESS_KEY_ID', credentialsId: '14dd1bff-3295-4649-a919-3fc6ad57f627', secretKeyVariable: 'AWS_SECRET_ACCESS_KEY']]) {
      sh 'aws cloudformation describe-stack-resources --region us-east-1 --stack-name jenkins'
    }
    junit 'reports/*.xml'
  }
}
