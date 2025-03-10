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
                sh '''
                    echo "Skipping upload step since it's optional"
                    # Uncomment the next line if you want to upload to a real Arduino board
                    # arduino-cli upload -p COM3 --fqbn arduino:avr:uno MyProject
                '''
            }
        }

        stage('Push to GitHub') {
            steps {
                sh '''
                    git config --global user.email "vigneshjan03@gmail.com"
                    git config --global user.name "Vignesh Aravindh"
                    git add .
                    git commit -m "Automated build from Jenkins" || echo "No changes to commit"
                    git push origin main || echo "No changes to push"
                '''
            }
        }
    }
}
