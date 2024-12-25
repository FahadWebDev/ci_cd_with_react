pipeline {
    agent any
    stages {
        stage('Check User') {
            steps {
                sh 'whoami'
            }
        }
        stage('build') {
            steps {
                echo 'Building the software'
                // sh 'npm i'
                // sh  'npm run build'

                // MAKE ZIP OF DIST AND COPY INTO FOLDER (IN SINGLE SH COMMAND)
                 sh '''
                    cd dist && zip -r frontend-build.zip * cp frontend-build.zip /var/www/frontend/
                 '''
                // MAKE ZIP OF DIST AND COPY INTO FOLDER (IN MULTIPLE SH COMMAND)
                // sh 'cd dist && zip -r frontend-build.zip * && cp frontend-build.zip /var/www/frontend/'
                // sh 'cp dist/frontend-build.zip /var/www/frontend/'
            } 
        }
        stage('deploy') {
            steps {
                echo 'Deploying the software'
                sh 'cd /var/www/frontend && unzip -o frontend-build.zip'
                // sh 'sudo scp -r /dist/frontend-build.zip admin-user@13.61.114.173:/var/www/frontend/'
                // sh 'sudo ssh admin-user@13.61.114.173 "cd /var/www/frontend && unzip -o frontend-build.zip"'
                // sh 'systemctl restart nginx'
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
