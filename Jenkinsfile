pipeline {
  agent any
  def wildfly.hostname = http://wildfly1.wildfly-khw2r.10.4.48.114.xip.io
  def wildfly.port = 9990
  def wildfly.username = admin
  def wildfly.password = admindev12345
  env.PATH="${wildfly.hostname}:${wildfly.port}:${wildfly.username}:${wildfly.password}:${env.PATH}"
  stages {
    stage('Pull') {
      steps {
        git(url: 'https://github.com/ssrksiva/testpipeline8.git', branch: 'master', poll: true)
      }
    }

    stage('Check Java') {
      steps {
        sh 'java -version'
      }
    }

    stage('Clean') {
      steps {
        sh 'chmod +x mvnw'
        sh './mvnw -ntp clean -P-webpack'
      }
    }
    stage('Deliver for Development Environment') {
      
      steps {
	    sh './mvnw -ntp verify -P-webpack -Pprod -DskipTests && ./mvnw wildfly:deploy-only -Pstandalone-mode'
        
        }

      }
    }

  }
