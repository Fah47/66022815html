pipeline {
    agent any
    stages {      
        stage("Copy file to Docker server"){
            steps {
				
                sh "scp -r /var/lib/jenkins/workspace/testhtml/* root@43.208.25.201:~/html66022815"
            }
        }
        
        stage("Build Docker Image") {
            steps {
                //path yaml files
				ansiblePlaybook playbook: '/var/lib/jenkins/workspace/testhtml/playbooks/build.yaml'
            }    
        } 
        
        stage("Create Docker Container") {
            steps {
                //path yaml files
				ansiblePlaybook playbook: '/var/lib/jenkins/workspace/testhtml/playbooks/deploy.yaml'
            }    
        } 
    }
}
