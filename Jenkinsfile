pipeline {
  agent any
  tools {
    maven 'maven'
  }
  stages {
    stage ("clean up")
    {
      steps {
        deleteDir()
      }
    }
    stage ("Clone repo")
    {
      steps {
        sh "git clone https://github.com/AnasGara/ex2"
        
      }
    }
    stage ("generate backend image")
    {
      steps {
        dir("ex2"){
          sh "mvn clean install"
          sh "docker build -t ex2 ."
        }
      }
    }
    
    stage ("Run docker compose")
    {
      steps{
        dir("ex2"){
          sh "docker compose up -d"
        }
      }
    }
  }
}
