node {
    checkout scm

    docker.withRegistry('https://hub.docker.com', 'docker-hub') {
    /*
     * In order to communicate with the MySQL server, this Pipeline explicitly
     * maps the port (`3306`) to a known port on the host machine.
     */
    docker.image('mhrdev19/as').withRun('') { c ->
        sh 'echo ok'
    }
 }
}
