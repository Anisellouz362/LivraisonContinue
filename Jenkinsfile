pipeline {
  agent any
    stages {
        stage('Pull') {
             steps{
                script{
                    checkout([$class: 'GitSCM', branches: [[name: '*/master']],
                        userRemoteConfigs: [[
                            credentialsId: 'anis',
                            url: 'https://github.com/Anisellouz362/LivraisonContinue.git']]])
                }
            }
        }
 
      

         stage('install') {
             steps{
                script{
                    sh " npm install --save-dev @angular-devkit/build-angular"
                }
            }
        }
         stage('Build') {
             steps{
                script{
                    sh " ansible-playbook ansible/build.yml -i ansible/inventory/host.yml"
                }
            }}
		 stage('docker') {
             steps{
                script{
                    sh "ansible-playbook ansible/docker.yml -i ansible/inventory/host.yml "
                }
            }
        }
			}}
