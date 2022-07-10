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
                    //ansible-playbook tomcat-setup.yml
                    ansible-playbook -i hosts --private-key=key.pem install-book.yml
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
