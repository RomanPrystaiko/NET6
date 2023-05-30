pipeline {
  agent any
  stages {
    stage('Hello') {
      steps {
        echo 'Hello World'
      }
    }
    stage('build') {
      steps {
        echo 'build strted'
        bat 'dotnet restore HelloWorld/HelloWorld.sln'
      }
    }
  }
}