pipeline {
  agent any
  stages {
    stage('Hello') {
      steps {
        echo 'Hello World'
        sh "dotnet restore HelloWorld/HelloWorld.sln"
      }
    }
  }
}