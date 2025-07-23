pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/yourusername/sample-app.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Deploy') {
            steps {
                ansiblePlaybook credentialsId: 'ansible-ssh-key',
                                 inventory: 'inventory.ini',
                                 playbook: 'deploy.yml'
            }
        }
    }
}
