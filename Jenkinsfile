pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/VigneshAravindh/arduino_ci_cd.git'
            }
        }

        stage('Compile Arduino Sketch') {
            steps {
                script {
                    sh 'arduino-cli compile --fqbn arduino:avr:uno MyProject'
                }
            }
        }

        stage('Upload to Arduino (Optional)') {
            steps {
                script {
                    // Uncomment if using a real Arduino board
                    // sh 'arduino-cli upload -p COM3 --fqbn arduino:avr:uno MyProject'
                }
            }
        }

        stage('Push to GitHub') {
            steps {
                script {
                    sh 'git add .'
                    sh 'git commit -m "Automated build from Jenkins" || echo "No changes to commit"'
                    sh 'git push origin main || echo "No changes to push"'
                }
            }
        }
    }
}
