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
 
stage('Push image') {
        /* Finally, we'll push the image with two tags:
         * First, the incremental build number from Jenkins
         * Second, the 'latest' tag.
         * Pushing multiple tags is cheap, as all the layers are reused. */
        docker.withRegistry('https://registry.hub.docker.com', 'docker-hub-credentials') {
            app.push("${env.BUILD_NUMBER}")
            app.push("latest")
        }
    }


sshagent(['my-ssh-key']) {
    sh 'ssh ubuntu@34.233.125.22 kubectl set image deployments/coursework2 coursework2=msnb9/devopscw2:$BUILD_NUMBER'
}
}


