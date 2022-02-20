pipeline {
    agent {
    docker { 
            image 'sravangcpdocker/ansible-gcp:1'
            args '-u root:root'
          }
        }
    stages {
        stage('Cloning Git') {
            steps {
                sh '''
                    #!/bin/bash
                    git clone https://github.com/sravan-github/tomcat-ansible.git
                    ls -l
                    ansible-playbook shell.yml
                    '''
                }
           }
        }
        post {
        always {
            cleanWs deleteDirs: true
        }
     }
}
