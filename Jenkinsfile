Jenkinsfile (Declarative Pipeline)

/* Requires the Docker Pipeline plugin */
pipeline {
    agent { docker { image 'maven:3.9.9-eclipse-temurin-21-alpine' } }
    stages {
        stage('build') {
            steps {
                sh 'mvn --version'
            }
        }
	    stage('test') {
            steps {
                retry(3) {
	                sh 'echo "Hello World"'
                }

                timeout(time: 3, unit: 'MINUTES') {
                    sh '''
                    echo "Multile shell steps example
                    ls -lah
                    '''
                }

                timeout(time: 5, unit: 'MINUTES') {
                    retry(5) {
                        sh 'echo will retry 5 times with 5 min timeout'
                    }
                }   
	        }
        }
    }
}

