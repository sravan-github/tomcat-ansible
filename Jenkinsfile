pipeline {
   //agent any
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
                    ansible --version
                    ansible-vault decrypt asuspem.pem --vault-password-file passwd --output key.pem
                    #ansible-playbook tomcat-setup.yml
                    ansible-playbook -i hosts --private-key=key.pem tomcat-setup.yml
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
