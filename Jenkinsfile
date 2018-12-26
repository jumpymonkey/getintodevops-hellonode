node {
    def app

    def rtServer = Artifactory.server 'ArtifactoryLab'
    def rtDocker = Artifactory.docker server: rtServer

    stage('Clone repository') {
        /* Let's make sure we have the repository cloned to our workspace */

        checkout scm
    }

    stage('Build image') {
        /* This builds the actual image; synonymous to
         * docker build on the command line */

        app = docker.build("docker-local/getintodevops-hellonode")
    }


    stage('Push image') {
        def buildInfo = rtDocker.push("docker-local/getintodevops-hellonode", "docker-local") 
        rtServer.publishBuildInfo buildInfo


    }
}
