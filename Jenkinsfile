pipeline
{
	agent any
		stages{
			stage('Pull') {
				steps{
					script{
						checkout([$class: 'GitSCM', branches: [[name: '*/master']],
							userRemoteConfigs: [[
								credentialsId: 'anis'
								url: 'https://github.com/Anisellouz362/LivraisonContinue.git']]])
							}
						}
					}
				}
			}
