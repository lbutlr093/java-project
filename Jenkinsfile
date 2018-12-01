node('linux') {
  stage('Test') {
    git 'https://github.com/lbutlr093/java-project.git'
    sh 'ant -f test.xml -v'
    junit 'reports/*.xml'
  }
  stage('Build') {
    sh 'ant -f build.xml -v'
  }
  stage() {
    //s3Upload(file:'rectangle-7.jar', bucket:'assignment10-bucket', path:'/workspace/java-pipeline/dist/rectangle-7.jar')
  }
  stage('Results') {
    junit 'reports/*.xml'
  }
}
