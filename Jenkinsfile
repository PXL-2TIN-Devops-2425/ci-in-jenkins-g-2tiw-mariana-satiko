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
        stage('Code Pull') {
            steps {
                //Get code from GitHub
               git branch: 'main', 
                url: 'git@github.com:malvesdiniz/calculator-app-finished.git'
            }
        }
         stage('Build') {
            steps {
                echo "Performing npm build"
                sh 'npm install'
            }
        }
        //stage('Unittest') {
            //steps {
            //    sh 'npm test' 
             //   junit '**/target/surefire-reports/TEST-*.xml' 
           // }
       // }
    }
}
        

