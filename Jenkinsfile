pipeline{
    agent any
    tools{nodejs 'Node 12'}
    stages{
        stage('Clone Repository From github'){
            steps{
                git 'https://github.com/jnkiarie/gallery.git'
            }
        }

        stage('Install Dependencies'){
            steps{
                sh 'npm install'
                sh 'npm install body-parser@1.19.0'
                sh 'npm install ejs@3.1.3'
                sh 'npm install express@4.17.1'
                sh 'npm install mongodb@3.5.8'
                sh 'npm install mongoose@5.9.16'
                sh 'npm install multer@1.4.2'
                sh 'npm install uuid@8.1.0'
            }
        }
        stage('Build App'){
            steps{
                sh 'npm build'
            }
        }
        stage('Deploy to Heroku'){
            steps{
                withCredentials([usernameColonPassword(credentialsId: 'gallery', variable: 'HEROKU_CREDENTIALS' )]){
                sh 'git push https://${HEROKU_CREDENTIALS}@git.heroku.com/gallery-l.git master'              
                }
            }
        }     
    }
}