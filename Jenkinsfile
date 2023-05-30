pipeline {
  agent any
  stages {
    stage('Hello') {
      steps {
        echo 'Hello World'
      }
    }
    stage('restore') {
      steps {
        bat 'dotnet restore HelloWorld/HelloWorld.sln'
      }
    }
   stage('clean') {
      steps {
        bat 'dotnet clean HelloWorld/HelloWorld.sln --configuration Release'
      }
    }
   stage('build') {
      steps {
        bat 'dotnet build HelloWorld/HelloWorld.sln --configuration Release --no-restore'
      }
    }
   stage('publish windows') {
      steps {
        bat 'dotnet publish HelloWorld/HelloWorld.sln --configuration Release'
        script{
        zip zipFile:"HelloWorld_win_x64.zip", dir:'HelloWorld/HelloWorld/bin/Release/net6.0/publish'

        archiveArtifacts "HelloWorld_win_x64.zip"
        }
      }
    }
   stage('publish linux') {
      steps {
        bat 'dotnet publish  HelloWorld/HelloWorld.sln --configuration Release --runtime ubuntu.18.04-x64 --self-contained true'
   	  script{
          zip zipFile:"HelloWorld_linux_x64.zip", dir:'HelloWorld/HelloWorld/bin/Release/net6.0/ubuntu.18.04-x64/publish'

          archiveArtifacts "HelloWorld_linux_x64.zip"
        }
      }
    }
  }
}