node {

    stage('SCM Checkout'){
        git credentialsId: 'ed29f538-e3c6-4269-8a50-4c8123667874', url: 'https://github.com/berkansasmaz/bestcloudforme-internship-application'
    }
    
        stage('MVN Package'){
            def mvnHome = tool name: 'maven-3', type: 'maven'
            def mvnCMD = "${mvnHome}/bin/mvn"
            sh label: '', script: "${mvnCMD} clean package"
        }

dockerNode(dockerHost: 'dockerhub', image: 'https://hub.docker.com/repository/docker/berkansasmaz/bestcloudforme-internship-application') {
        checkout scm
    
        docker.withRegistry('https://registry.hub.docker.com', 'dockerHub') {
    
            def customImage = docker.build("berkansasmaz/bestcloudforme-internship-application")
    
            /* Push the container to the custom Registry */
            customImage.push()
        }
}
   
}