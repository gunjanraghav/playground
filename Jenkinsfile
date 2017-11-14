pipeline {
  agent {
    node {
      label 'maven-jdk-8'
    }
    
  }
  stages {
    stage('idk') {
      parallel {
        stage('Preparation') {
          steps {
            git(url: 'https://github.com/jglick/simple-maven-project-with-tests.git', branch: 'master')
            sh 'echo "hello"'
          }
        }
        stage('idk') {
          steps {
            sleep 10
          }
        }
      }
    }
    stage('Build') {
      steps {
        sh 'mvn -Dmaven.test.failure.ignore clean package'
      }
    }
    stage('Result') {
      steps {
        junit '**/target/surefire-reports/TEST-*.xml'
        archiveArtifacts 'target/*.jar'
      }
    }
  }
}