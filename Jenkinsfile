pipeline {
    agent any

    environment {
        NODEJS_HOME = tool 'NodeJS'
        PATH = "${NODEJS_HOME}/bin:${env.PATH}"
    }

    stages {
        stage('Checkout') {
            steps {
                script {
                    // Ensuring we fetch the correct branch (main)
                    checkout([
                        $class: 'GitSCM', 
                        branches: [[name: '*/main']],  // Ensure this matches your branch name
                        userRemoteConfigs: [[url: 'https://github.com/RakshitYadav09/MyApp-CI-CD.git']]
                    ])
                }
            }
        }

        stage('Install Dependencies') {
            steps {
                bat 'npm install'  // Use `sh` if on Linux/macOS
            }
        }

        stage('Build') {
            steps {
                bat 'npm run build'  // Use `sh` if on Linux/macOS
            }
        }

        stage('Test') {
            steps {
                bat 'npm test'  // Use `sh` if on Linux/macOS
            }
        }

        stage('Deploy') {
            steps {
                echo "Deploying application..."  // Replace with actual deploy steps
                // Example: sh 'deploy-command'
            }
        }
    }
}
