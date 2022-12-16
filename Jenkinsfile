node {
    def app

    stage('Clone repositry') {
       /* testing */
        checkout scm
    }


 stage('Build image') {
        /* This builds the actual image; synonymous to
         * docker build on the command line */

      app = docker.build("msnb9/devopscw2")
    }
 stage('Test image') {
        /* Testing container to be launched from image */

        app.inside {
            sh 'echo "Tests passed"'
        }
    }
}

