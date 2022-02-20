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
                    git clone https://github.com/sravan-github/test-jenkins.git
                    cd test-jenkins
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
