pipeline {
    agent any
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

            agent {
              docker {
                 image 'httpd:latest'
              }
    }

        stage("Test") {
/*	    agent {
              docker {
                 image 'httpd:latest'
              }
    }*/
            when {
                environment name: "FOO", value: "bar"
            }
/*            options {
                timeout(time: 15, unit: "SECONDS")
            }*/
            steps {
                sh 'apache2ctl -t'
            }
        }
    }
}

