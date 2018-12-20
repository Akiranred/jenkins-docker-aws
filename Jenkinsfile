pipeline {
    agent {
        docker { image 'node:7-alpine' }
    }
    stages {
        stage('Test') {
            steps {
                sh 'node --version'
            }
        }
        
	stage('Build Image') {
            steps {
                sh 'docker build -t ravi2krishna/docker-react -f Dockerfile.dev .'
            }
        }
	
	stage('Run Container') {
            steps {
                sh 'docker run ravi2krishna/docker-react npm run test -- --coverage'
            }
        }
    }
}
