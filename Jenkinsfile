pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                git url: 'https://github.com/VigneshAravindh/arduino_ci_cd.git', branch: 'main'
            }
        }

        stage('Compile Arduino Sketch') {
            steps {
                sh 'arduino-cli compile --fqbn arduino:avr:uno MyProject'
            }
        }

        stage('Upload to Arduino (Optional)') {
            steps {
                // Uncomment if using a real Arduino board
                // sh 'arduino-cli upload -p COM3 --fqbn arduino:avr:uno MyProject'
            }
        }

        stage('Push to GitHub') {
            steps {
                sh '''
                    git add .
                    git commit -m "Automated build from Jenkins" || echo "No changes to commit"
                    git push origin main || echo "No changes to push"
                '''
            }
        }
    }
}
