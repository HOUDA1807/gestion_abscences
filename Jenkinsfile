pipeline {
    agent any

    stages {
        stage('Info sur la machine') {
            steps {
                script {
                    sh 'hostname'
                    sh 'hostname -I'
                }
            }
        }

        stage('Checkout SCM') {
            steps {
                checkout scm
            }
        }

        stage('Exécution du playbook Ansible - Déploiement') {
            steps {
                script {
                    sh 'cd ansible && ansible-playbook -i inventory.ini playbooks/deploy.yml'
                }
            }
        }
    }

    post {
        always {
            echo 'Le pipeline a terminé.'
        }
        success {
            echo 'Le pipeline a réussi!'
        }
        failure {
            echo 'Le pipeline a échoué.'
        }
    }
}
