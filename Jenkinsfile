node {

    checkout scm

    docker.withRegistry('https://registry.hub.docker.com', 'dockerHub') {

        def customImage = docker.build("berkansasmaz/bestcloudforme-internship-application")

        /* Push the container to the custom Registry */
        customImage.push()
    }
}