node('linux') {
  stage('can i call this whatever') {
    git 'https://github.com/lbutlr093/java-project.git'
    sh 'ant -f test.xml -v'
    junit 'reports/*.xml'
  }
  stage('Build') {
    sh 'ant -f build.xml -v'
  }
  stage('Results') {
    junit 'reports/*.xml'
  }
}
