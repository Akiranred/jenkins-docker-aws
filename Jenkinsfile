pipeline {
    agent none    
    stages {
        stage('Test') {
	    agent { docker 'node:7-alpine'}
            steps {
                sh 'node --version'
            }
        }
        
	stage('Build Image') {
	    agent any
            steps {
                sh 'docker build -t ravi2krishna/docker-react -f Dockerfile.dev .'
            }
        }
	
	stage('Run Container') {
	    agent any
            steps {
                sh 'docker run ravi2krishna/docker-react npm run test -- --coverage'
            }
        }
    }
}
