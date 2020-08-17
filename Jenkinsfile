pipeline {

  agent any
  environment {
    //adding a comment for the commit test
    DEPLOY_CREDS = credentials('deploy-anypoint-user')
    MULE_VERSION = '4.1.4'
    WORKER = "Micro"
  }
  stages {
    stage('Build') {
      steps {
            bat 'mvn -B -U -e -V clean -DskipTests package'
      }
    }

    stage('Test') {
      steps {
          bat "mvn test"
      }
    }

     stage('Deploy Development') {
      environment {
        ENVIRONMENT = 'Sandbox'
        APP_NAME = 'mule-jenkins-jfrog1'
      }
      steps {
            bat 'mvn -U -V -e -B -DskipTests deploy -DmuleDeploy -Dmule.version="4.3.0" -Danypoint.username="RamaraoTech" -Danypoint.password="Tech@2020" -Dcloudhub.app="mule-jenkins-jfrog1" -Dcloudhub.environment="sandbox" -Dcloudhub.worker="1"'
      }
    }
    
      }
          }
  
  tools {
    maven 'M3'
  }
