pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'WDC-V2', url: 'https://github.com/JunandaDeyastusesa/komputasi-awan-1'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'ansible-playbook -i inventory/hosts requirement.yml'
            }
        }

        stage('Deploy Application') {
            steps {
                sh 'ansible-playbook -i inventory/hosts playbooks/deploy.yml'
            }
        }

        stage('Database Setup') {
            steps {
                sh 'ansible-playbook -i inventory/hosts playbooks/mysql.yml'
            }
        }

        stage('Testing') {
            steps {
                sh './vendor/bin/phpunit'
            }
        }
    }
}
