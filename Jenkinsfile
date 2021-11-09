node {
    def app

    stage('Clone repository') {
        /* Cloning the Repository to our Workspace */

        checkout scm
    }
	stage('Build')
	{
		steps {
      script{
			sh "ansible-playbook ansible/build.yml -i ansible/inventory/host.yml"
			}
      }
			}
}
