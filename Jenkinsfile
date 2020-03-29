node {

    checkout scm

    docker.withRegistry('https://registry.hub.docker.com', '93377ffb-c034-44dd-a645-f8600470fd8f') {

        def customImage = docker.build("berkansasmaz/bestcloudforme-internship-application")

        /* Push the container to the custom Registry */
        customImage.push()
    }
}