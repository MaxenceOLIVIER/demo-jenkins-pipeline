pipeline {
    agent any

    stages {

        stage('Test') {
            steps {
                echo 'Exécution des tests unitaires...'
                sh 'mvn test'
            }
            post {
                always {
                    echo 'Publication des résultats de tests...'
                    junit '**/target/surefire-reports/*.xml'
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
