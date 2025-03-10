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
                bat "\"C:\\Users\\vigne\\Downloads\\arduino-cli_1.2.0_Windows_64bit\\arduino-cli.exe\" compile --fqbn arduino:avr:uno MyProject"
            }
        }

        stage('Upload to Arduino (Optional)') {
            steps {
                bat '''
                    echo "Skipping upload step since it's optional"
                    rem Uncomment the next line if you want to upload to a real Arduino board
                    rem "C:\\Users\\vigne\\Downloads\\arduino-cli_1.2.0_Windows_64bit\\arduino-cli.exe" upload -p COM3 --fqbn arduino:avr:uno MyProject
                '''
            }
        }

        stage('Push to GitHub') {
            steps {
                bat '''
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
