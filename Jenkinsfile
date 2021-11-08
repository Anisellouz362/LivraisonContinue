pipeline
{
	agent any
		stages{
			stage('Pull') {
				steps{
					script{
						checkout([$class: 'GitSCM', branches: [[name: '*/master']],
							userRemoteConfigs: [[
								credentialsId: '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'
								url: 'https://github.com/Anisellouz362/LivraisonContinue.git']]])
							}
						}
					}
				}
			}
