pipeline {
  agent any
    stages {
        stage('Pull') {
             steps{
                script{
                    checkout([$class: 'GitSCM', branches: [[name: '*/master']],
                        userRemoteConfigs: [[
                            credentialsId: '83efa891-b63a-4fdc-8e41-f61903d33ffd',
                            url: 'https://github.com/haifgh/devops.git']]])
                }
            }
        }
   	stage('Install') {
             steps{
                script{
                    sh "sudo npm install"
                }
            }
        }

	stage ('Build') {
	
			steps {
			
			sh "ansible-playbook ansible/build.yml -i ansible/inventory/host.yml"
	
			}


	}
	stage('docker') {
		steps{
			script {


			sh "ansible-playbook ansible/docker.yml -i ansible/inventory/host.yml "


}
}
}
stage('docker_registry') {
steps{
script {


sh "ansible-playbook ansible/docker-registry.yml -i ansible/inventory/host.yml "


}
}
}

}
}
