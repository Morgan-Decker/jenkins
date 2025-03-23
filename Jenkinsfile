// Jenkinsfile (Declarative Pipeline)

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
    post {
        always {
            echo 'This will always run'
        }
        success {
            echo 'This will run only if successful'
        }
        failure {
            echo 'This will run only if failed'
        }
        unstable {
            echo 'This will run only if the run was marked as unstable'
        }
        changed {
            echo 'This will run only if the state of the Pipeline has changed'
            echo 'For example, if the Pipeline was previously failing but is now successful'
        }
    }
}

