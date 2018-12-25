pipeline {
    agent none    
    stages {
	    
	stage('Build Image') {
	    agent any
            steps {
                sh 'docker build -t ravi2krishna/docker-react .'
            }
        }
	
	stage('Deploy AWS Beanstalk') {
	    agent any
	    steps {
                script {
                GIT_COMMIT = sh (script: "git log -n 1 --pretty=format:'%H'", returnStdout: true)
                }
                echo "GIT_COMMIT is $GIT_COMMIT"
                step([$class: 'AWSEBDeploymentBuilder', applicationName: 'docker', awsRegion: 'us-east-1', bucketName: 'elasticbeanstalk-us-east-1-256225485494', checkHealth: true, credentialId: 'react-app', environmentName: 'Docker-env', excludes: '', includes: '', keyPrefix: '', maxAttempts: 5, rootObject: '', sleepTime: 90, versionDescriptionFormat: 'app', versionLabelFormat: 'myapp', zeroDowntime: false])
            }
        }
    }
}
