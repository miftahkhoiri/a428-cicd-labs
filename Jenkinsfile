pipeline {
    agent {
        docker {
            image 'node:16-buster-slim'
            args '-p 3000:3000'
            args '-u root'
        }
    }
    stages {
        stage('Build') {
            steps {
                sh 'npm install'
            }
        }
        stage('Test') {
            steps {
                sh 'sh ./jenkins/scripts/test.sh'
            }
        }
        stage('Deploy') {

            steps {          
                sh 'sh ./jenkins/scripts/deliver.sh'
                input message: 'Sudah selesai menggunakan React App? (Klik "Proceed" untuk mengakhiri)'
                sh 'sh ./jenkins/scripts/kill.sh'
            }

        }
    }
}
