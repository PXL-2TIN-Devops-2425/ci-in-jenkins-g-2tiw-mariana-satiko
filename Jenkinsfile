pipeline {
    agent any
    tools {
        nodejs 'TINnode-devops'
    }
    stages {
        stage('opdracht 5') {
            steps {
                echo "good luck..."
            }
        }
        stage('Fetching Source') {
            steps {
               git branch: 'main', url: 'git@github.com:malvesdiniz/calculator-app-finished.git'
            }
        }
         stage('Install Dependencies') {
            steps {
                script {
                    sh 'npm install'
                }
            }
        }
        stage('Unittest') {
            steps {
                sh 'npm test' 
                junit 'test-report.xml' 
            }
        }
    }
}
        

