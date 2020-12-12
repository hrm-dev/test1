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
		sh 'touch test1'
                sh 'printf "\\e[31mSome code compilation here...\\e[0m\\n"'
            }
        }

        stage("Test") {
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

