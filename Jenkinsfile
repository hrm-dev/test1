node {
    checkout scm

    docker.withRegistry('https://index.docker.io/v2', 'docker-hub') {
    /*
     * In order to communicate with the MySQL server, this Pipeline explicitly
     * maps the port (`3306`) to a known port on the host machine.
     */
    docker.image('mhrdev19/as').withRun('') { c ->
        sh 'echo ok'
    }
 }
}
