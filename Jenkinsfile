node {
    def app

    stage('Testing step') {
       /* testing */
        checkout scm
    }
}

 stage('Build image') {
        /* This builds the actual image; synonymous to
         * docker build on the command line */

        app = docker.build("MsnB9/DevOpsCW2")
    }
