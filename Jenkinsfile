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

        stage("Test") {
	     agent {
        docker {
                image 'test/as:latest'
                args  '-d -p 8111:80'
        }
     }

            when {
                environment name: "FOO", value: "bar"
            }
            options {
                timeout(time: 15, unit: "SECONDS")
            }
            steps {
                sh 'apache2ctl -t'
            }
        }
    }
}

