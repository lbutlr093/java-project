node('linux') {
  stage('Unit Tests') {
    git 'https://github.com/lbutlr093/java-project.git'
    sh 'ant -f test.xml -v'
    junit 'reports/result.xml'
  }
  stage('Build') {
    sh 'ant -f build.xml -v'
  }
  stage('Results') {
    junit 'reports/*.xml'
  }
}
