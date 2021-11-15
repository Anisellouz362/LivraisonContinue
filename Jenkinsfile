
pipeline {
  agent any
    stages {
        stage('Pull') {
             steps{
                script{
                    checkout([$class: 'GitSCM', branches: [[name: '*/master']],
                        userRemoteConfigs: [[
                            credentialsId: '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',
                            url: 'https://github.com/Anisellouz362/LivraisonContinue.git']]])
                }
            }
        }
      

         stage('install') {
             steps{
                script{
                    sh " npm install --save-dev @angular-devkit/build-angular --force"
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
    stage('Deploy Image') {
      steps{
         script {
          docker.withRegistry('https://registry.hub.docker.com', 'anisellouz') {
                    sh "ansible-playbook ansible/docker-registry.yml -i ansible/inventory/host.yml "
                    sh "docker push anisellouz/devops"
          }
        }
      }
    }
			}}
