pipeline {
    /* ↪ Exécution sur un agent Docker avec Node.js */
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo 'Clonage du dépôt GitHub...'
                checkout scm
            }
        }

        stage('Install dependencies') {
            steps {
                echo 'Installation des dépendances Node.js...'
                sh 'npm install'
            }
        }

        stage('Run tests') {
            steps {
                echo 'Exécution des tests Jest...'
                sh 'npm test'
            }
            post {
                always {
                    echo 'Publication des résultats de tests...'
                    junit 'reports/junit.xml'
                }
            }
        }
    }

    post {
        success {
            echo 'Build terminé avec succès !'
        }
        failure {
            echo 'Build échoué.'
        }
        always {
            echo 'Pipeline terminé (quel que soit le statut).'
        }
    }
}