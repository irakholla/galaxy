pipeline {
    agent any
    stages {
        stage("ansible_galaxy") {
            steps {
                sh """
                mkdir -p roles
                ansible-galaxy install -p roles -r requirements.yml
                """
                ansiblePlaybook(playbook: 'galaxy_playbook.yml', inventory: 'hosts')
            }         
        }
        stage("tests") {
            steps {
                ansiblePlaybook(playbook: 'test_playbook.yml', inventory: 'hosts')
            }          
        }        
    }
}
