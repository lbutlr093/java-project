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
    s3Upload(bucket:"assignment10-bucket", file:'rectangle-6.jar', path:'rectangle-6.jar')
  }
  
  stage('Results') {
    junit 'reports/*.xml'
  }
}
