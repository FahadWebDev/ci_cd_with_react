pipeline {
    agent any

    stages {
        stage('build') {
            steps {
                echo 'Building the software'
                bat 'npm install'
                bat 'npm run build'
            } 
        }
        stage('deploy') {
            steps {
                echo 'Deploying the software'
                // Add any Windows-specific deployment steps here
            }
        } 
    }
    post {
        success {
            echo 'Build succeeded'
        }
        failure {
            echo 'Build failed'
        }
    }
}
