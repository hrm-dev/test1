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
	//	sh 'docker build -t asd .'
		script {
                	dockerImage = docker.build imagename + ":$BUILD_NUMBER" 
		}

            }
        }

        stage("Test") {
	    agent {
              docker { 
		image 'httpd:latest' 
		args '-p 9091:80 -d'
	      }
    	    }
            steps {
                sh 'apache2ctl -t'
            }
        }
    }
}

