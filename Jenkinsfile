node {
    checkout scm

    docker.withRegistry('https://hub.docker.com', '72750895-e960-4fdb-90d6-e9b46717d1e7') {
    /*
     * In order to communicate with the MySQL server, this Pipeline explicitly
     * maps the port (`3306`) to a known port on the host machine.
     */
    docker.image('mhrdev19/as').withRun('') { c ->
        sh 'echo ok'
    }

}
