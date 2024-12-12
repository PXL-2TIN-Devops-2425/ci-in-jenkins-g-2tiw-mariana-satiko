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
        stage('fetching source') {
            steps {
                //Get code from GitHub
               git branch: 'main', 
                url: 'git@github.com:malvesdiniz/calculator-app-finished.git'
            }
        }
         stage('install dependencies') {
            steps {
                echo "Performing npm build"
                sh 'npm install'
            }
        }
        stage('unittest') {
            steps {
                sh 'npm test'
                junit 'test-results.xml'
            }
        }   
    }
}
        

