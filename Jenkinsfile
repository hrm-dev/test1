pipeline {
    agent none
//    agent { dockerfile true }

    environment {
        FOO = "bar"
        imagename = "test/as"
        dockerImage = ''
    }


    stages {
        stage("Build") {
            options {
                timeout(time: 1, unit: "MINUTES")
            }
            steps {
		script {
                	dockerImage = docker.build imagename + ":$BUILD_NUMBER" 
		}

            }
        }

        stage("Test") {
	    agent {
              docker { image 'httpd:latest' }
    	    }
            steps {
                sh 'apachectl -t'
            }
        }
    }
}

