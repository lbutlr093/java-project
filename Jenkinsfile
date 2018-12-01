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
    sh 'aws cloudformation describe-stack-resources --region us-east-1 --stack-name jenkins'
    junit 'reports/*.xml'
  }
}
