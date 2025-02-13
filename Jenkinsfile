pipeline {
    agent any
    stages {      
        stage("Copy file to Docker server") {
            steps {
                sh "scp -r /var/lib/jenkins/workspace/66022815html/* root@43.208.25.201:~/66022815html"
            }
        }

        stage("Build Docker Image") {
            steps {
                ansiblePlaybook playbook: '/var/lib/jenkins/workspace/66022815html/playbooks/build.yaml'
            }
        }

        stage("Check Docker Image") {
            steps {
                sh "ssh root@43.208.25.201 'docker images | grep 66022815html-neogym || exit 1'"
            }
        }

        stage("Create Docker Container") {
            steps {
                ansiblePlaybook playbook: '/var/lib/jenkins/workspace/66022815html/playbooks/deploy.yaml'
            }
        }
    }
}
