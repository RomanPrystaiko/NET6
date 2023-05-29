pipeline {
  agent any
  stages {
    stage('Hello') {
      parallel {
        stage('Hello') {
          steps {
            echo 'Hello World'
            sh 'dotnet restore HelloWorld/HelloWorld.sln'
          }
        }

        stage('build') {
          agent any
          steps {
            dotnetPublish()
          }
        }

      }
    }

  }
}