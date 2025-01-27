pipeline {
    agent any

    stages {
        stage('cloning Git Repository') {
            steps {
                git branch: 'main', url: 'https://github.com/biragtr/-jk-public-gh.git'
            }
        }
        
        stage('Building Image') {
            steps {
                sh 'docker build -t webapp:${BUILD_NUMBER} .'
            }
        } 
        
        stage('Deploying Application') {
            steps {
                sh '''
                #docker stop webapp_ctr
                sh docker run --rm -d -p 3000:3000 --name webapp_ctr webapp:${BUILD_NUMBER}
            '''
            }    
        }
    }
}
