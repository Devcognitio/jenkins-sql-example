@Library("devops-shared-functions") _

pipeline {
    agent any

stages {
    stage('Build') {
        steps {
            checkout scm
            sh './gradlew -version'
            sh './gradlew clean'
            sh './gradlew build'
        }
    }
    
    stage('BDScriptsExecution') {
        steps {
            script {
                def dbHost = '172.17.0.2'
                def dbPort = '1433'
                bdExecute('/bd/scripts', '/bd/config.json', dbHost, dbPort)
            }
        }
     }
    
   }
}
