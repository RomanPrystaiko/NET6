pipeline {
  agent any
  stages {
    stage('Hello') {
      steps {
        echo 'Hello World'
        sh "dotnetRestore HelloWorld/HelloWorld.sln"
      }
    }
  }
}