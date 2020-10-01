pipeline {
  agent any
  stages {
    stage('Pull') {
      steps {
        git(url: 'https://github.com/ssrksiva/testpipeline5.git', branch: 'develop', poll: true)
      }
    }

    stage('Check Java') {
      steps {
        sh 'java -version'
      }
    }

    stage('Deliver for Development Environment') {
      
      steps {
	    sh './mvnw -ntp verify -P-webpack -Pprod -DskipTests'
        sh './mvnw wildfly:deploy-only -Pstandaone-mode'
        }

      }
    }

  }
