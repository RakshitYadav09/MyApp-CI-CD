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
                        branches: [[name: '*/main']],  // Change 'main' to your branch if necessary
                        userRemoteConfigs: [[url: 'https://github.com/RakshitYadav09/MyApp-CI-CD.git']]
                    ])
                }
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Build') {
            steps {
                sh 'npm run build'
            }
        }

        stage('Test') {
            steps {
                sh 'npm test'
            }
        }

        stage('Deploy') {
            steps {
                echo "Deploying application..."
                // Add deployment steps here
            }
        }
    }
}
