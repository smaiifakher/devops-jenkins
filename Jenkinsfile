pipeline {
    agent any
    tools {nodejs "nodejs"}
    stages {
        stage('Pull') {
             steps{
                script{
                    checkout([$class: 'GitSCM', branches: [[name: '*/main']],
                        userRemoteConfigs: [[
                            credentialsId: '312f845b-c93f-40bf-989e-b0db8200e41a',
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
        stage ('code quality'){
            steps{
                sh 'ng lint'
            }
        }

        stage('Serve') {
            steps{
                script{
                    sh "ng serve --open"
                }
            }
        }
    }
}
