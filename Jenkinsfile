pipeline {
    agent any
    stages {      
        stage("Copy file to Docker server"){
            steps {
				
                sh "scp -r /var/lib/jenkins/workspace/66022815lab/* root@43.208.25.201:~/66022815lab"
            }
        }
        
        stage("Build Docker Image") {
            steps {
                //path yaml files
				ansiblePlaybook playbook: '/var/lib/jenkins/workspace/66022815lab/playbooks/build.yaml'
            }    
        } 
        
        stage("Create Docker Container") {
            steps {
                //path yaml files
				ansiblePlaybook playbook: '/var/lib/jenkins/workspace/66022815lab/playbooks/deploy.yaml'
            }    
        } 
    }
}
