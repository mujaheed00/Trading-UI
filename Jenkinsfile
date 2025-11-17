pipeline {
    agent any

    stages {
        stage('Git checkout') {
            steps {
                git 'https://github.com/pmohd6065-ux/Trading-UI.git'
            }
        }

        stage('Install npm prerequisites') {
            steps {
                // Skip npm audit completely for CI speed and stability
                sh 'npm install --no-audit'

                sh 'npm run build'

                // Navigate to the build folder properly in Jenkins
                dir('build') {
                    sh 'pm2 --name Trading-UI start npm -- start'
                }
            }
        }
    }
}
