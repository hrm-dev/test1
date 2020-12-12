pipeline {
    agent any
//    agent { dockerfile true }

    environment {
        FOO = "bar"
    }


    stages {
        stage("Build") {
            options {
                timeout(time: 1, unit: "MINUTES")
            }
            steps {
		sh 'docker build -t asd .'
            }
        }

        stage("Test") {
	     agent {
        docker {
                image 'maven:3-alpine'
                label 'my-defined-label'
                args  '-v /tmp:/tmp'
        }
     }

            when {
                environment name: "FOO", value: "bar"
            }
            options {
                timeout(time: 2, unit: "MINUTES")
            }
            steps {
                sh 'printf "\\e[31mSome tests execution here...\\e[0m\\n"'
            }
        }
    }
}

