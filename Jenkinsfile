node {
    def app

    stage('Pobranie repo') {
        checkout scm
    }

    stage('Buduj obraz') {
        app = docker.build("mhrdev19/as")
    }
    stage('Testy') {
        docker.image('mhrdev19/as').withRun('') { c ->
            sh 'echo asd'
    	}

    }

    /*stage('Push image') {
        /* 
			You would need to first register with DockerHub before you can push images to your account
		*/
        docker.withRegistry('https://registry.hub.docker.com', 'docker-hub') {
            app.push("${env.BUILD_NUMBER}")
            app.push("latest")
            } 
                echo "Trying to Push Docker Build to DockerHub"
    }*/
}

