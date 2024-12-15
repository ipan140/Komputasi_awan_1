pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'iya', url: 'https://github.com/ipan140/Komputasi_awan_1'
            }
        }

        stage('Install Dependencies') {
            steps {
                bath 'ansible-playbook -i inventory/hosts requirement.yml'
            }
        }

        stage('Deploy Application') {
            steps {
                bath 'ansible-playbook -i inventory/hosts playbooks/deploy.yml'
            }
        }

        stage('Database Setup') {
            steps {
                bath 'ansible-playbook -i inventory/hosts playbooks/mysql.yml'
            }
        }

        stage('Testing') {
            steps {
                bath './vendor/bin/phpunit'
            }
        }
    }
}
