pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/ankamraghu27/gravity-assesment.git', branch: 'main'
            }
        }

        stage('Build') {
            steps {
                sh 'chmod +x build.sh'
                sh './build.sh'
            }
        }

        stage('Test') {
            steps {
                sh 'chmod +x test.sh'
                sh './test.sh'
            }
        }

        stage('Deploy') {
            steps {
                // Copy app files to web server folder (update path if needed)
                sh 'sudo cp -r * /var/www/html/'
                // Restart nginx to serve the new app
                sh 'sudo systemctl restart nginx'
            }
        }
    }
}
