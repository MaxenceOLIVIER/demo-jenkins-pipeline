pipeline {
    agent {
        docker {
            image 'maven:4.0.0-rc-4-sapmachine-25'
        }
    }

    stages {
        stage('Build & Test') {
            steps {
                sh 'mvn clean test'
            }
        }
    }

    post {
        success {
            echo '✅ Build succeeded!'
        }
        failure {
            echo '❌ Build failed!'
        }
    }
}
 