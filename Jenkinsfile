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
                echo "Performing npm build..."
                sh 'npm install'
            }
        }
        stage('unittest') {
            steps {
                echo "running unitests..."
                sh 'npm test'
                junit 'junit.xml'
            }
        }   
        stage('create bundle') {
            steps {
                echo "Creating the bundle directory..."
                sh '''
                mkdir -p bundle
                rsync -av 
                --exclude='bundle' 
                --exclude='.git' 
                --exclude='.gitignore' 
                --exclude='readme.md' 
                --exclude='Jenkinsfile' 
                --exclude='tests'
                ./ bundle/
                '''
                echo "Zipping the bundle directory..."
                sh 'zip -r bundle.zip bundle'
            }
        }
    }
}
        

