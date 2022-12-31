pipeline {
  agent any
    stages {
        stage('Pull') {
             steps{
                script{
                    checkout([$class: 'GitSCM', branches: [[name: '*/main']],
                        userRemoteConfigs: [[
                            credentialsId: '9b3b41b7-7b37-4a59-a606-3955382c919e',
                            url: 'https://github.com/smaiifakher/devops-jenkins.git']]])
                }
            }
        }
        stage('Install') {
             steps{
                script{
                    sh "npm install"
                }
            }
        }
        stage('Version') {
            steps{
                script{
                    sh "ng version"
                }
            }
        }
         stage('Test') {
             steps{
                script{
                    sh "ng test --watch=false"
                }
            }
        }
        stage('Serve') {
            steps{
                script{
                    sh "ng serve"
                }
            }
        }
    }
}