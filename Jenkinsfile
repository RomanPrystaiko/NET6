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
        bat 'dotnet publish HelloWorld/HelloWorld.sln --configuration Release  --no-restore --runtime win-x64 --self-contained true'

     bat 'zip -r HelloWorld-win-x64.zip HelloWorld/HelloWorld/bin/Release/net7.0/win-x64/publish'
      }
    }
   stage('publish linux') {
      steps {
        bat 'dotnet publish  HelloWorld/HelloWorld.sln --configuration Release  --no-restore --runtime linux-x64 --self-contained true'
       bat 'zip -r HelloWorld-linux-x64.zip HelloWorld/HelloWorld/bin/Release/net7.0/linux-x64/publish'
      }
    }
  }
}