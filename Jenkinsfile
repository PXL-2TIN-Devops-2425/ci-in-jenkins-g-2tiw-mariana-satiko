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
        stage('cleanup') {
            steps {
                echo "Cleaning up old artifact..."
                sh 'rm -rf bundle bundle.zip'
            }
        }
        stage('fetching source') {
            steps {
                //Get code from GitHub
               git branch: 'main', 
                url: 'https://github.com/satikoshapy/calculator-app-finished.git'
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
                rsync -av  --exclude='bundle' --exclude='.git' --exclude='.gitignore' --exclude='readme.md' --exclude='Jenkinsfile' --exclude='tests' ./ bundle/
                '''
                echo "Zipping the bundle directory..."
                sh 'zip -r bundle.zip bundle'
            }
        }
    }
     post {
        failure {
            script {
                def errorMessage = "Pipeline failed try on ${new Date()}"
                writeFile file: "/var/lib/jenkins/jenkinserrorlog", text: errorMessage
            }
        }
        success {
            archiveArtifacts artifacts: 'bundle.zip', allowEmptyArchive: false
        }
    }
}
        

