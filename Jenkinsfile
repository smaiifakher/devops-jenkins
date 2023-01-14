pipeline {
    agent any
    tools {nodejs "nodejs"}
    stages {
        stage('Pull') {
             steps{
                script{
                    checkout([$class: 'GitSCM', branches: [[name: '*/main']],
                        userRemoteConfigs: [[
                            credentialsId: 'e2a83573-458d-47dc-8b99-676706b281dd',
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
                    sh "ansible-galaxy init build"
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
