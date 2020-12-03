node {
    def app

    stage('Pobranie repo') {
        checkout scm
    }

    stage('Buduj obraz') {
        app = docker.build("mhrdev19/as")
    }

#    stage('Testy') {
#        app.inside {
#            apache2ctl -t
#        }
#    }
      stage('Testy') {
        docker.image('centos:7').inside("--link ${c.id}:db") {
            /*
             * Run some tests which require MySQL, and assume that it is
             * available on the host name `db`
             */
            sh 'make check'
        }
      }

    stage('Push image') {
        /* 
			You would need to first register with DockerHub before you can push images to your account
		*/
        docker.withRegistry('https://registry.hub.docker.com', 'docker-hub') {
            app.push("${env.BUILD_NUMBER}")
            app.push("latest")
            } 
                echo "Trying to Push Docker Build to DockerHub"
    }
}

