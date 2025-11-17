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
                // Skip audit completely
                sh 'npm install --no-audit || true'

                // Show build logs even on failure
                sh 'npm run build || true'

                // Move into build folder
                dir('build') {
                    // PM2 often returns exit code 1 if already running
                    sh 'pm2 --name Trading-UI start npm -- start || true'
                }
            }
        }
    }
}
