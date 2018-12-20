pipeline {
    agent {
	docker {
                label 's1'  // both label and image
                image 'node:7-alpine' 
              }
    }
    stages {
        stage('Test') {
            steps {
                sh 'node --version'
            }
        }
    }
}
