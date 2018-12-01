node('linux') {
  stage('Unit Tests') {
    git 'https://github.com/lbutlr093/java-project.git'
    sh 'ant -f test.xml -v'
    junit 'reports/result.xml'
  }
  stage('Build') {
    sh 'ant -f build.xml -v'
  }
  stage() {
    s3Upload(file:'rectangle-5.jar', bucket:'assignment10-bucket', path:'http://assignment10-bucket.s3.amazonaws.com/rectangle.jar')  
  }
  
  stage('Results') {
    junit 'reports/*.xml'
  }
}
