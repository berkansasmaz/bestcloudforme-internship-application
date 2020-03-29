node {

    stage('SCM Checkout'){
        git credentialsId: 'github', url: 'https://github.com/berkansasmaz/bestcloudforme-internship-application'
        git (credentialsId: 'github', url: 'https://github.com/berkansasmaz/bestcloudforme-internship-application', branch: 'dev')
    }
    
    stage('MVN Package'){
        def mvnHome = tool name: 'maven-3', type: 'maven'
        def mvnCMD = "${mvnHome}/bin/mvn"
        sh label: '', script: "${mvnCMD} clean package"
    }

     stage('Docker Initialize'){
        def dockerHome = tool name: 'myDocker', type: 'org.jenkinsci.plugins.docker.commons.tools.DockerTool'
        env.PATH = "${dockerHome}/bin:${env.PATH}"
     }     

     stage('Docker Build Image'){
        sh 'docker build -t berkansasmaz/bestcloudforme-internship-application .'
     }     
        
      stage('Docker Push Image'){
        withCredentials([string(credentialsId: 'docker-pwd', variable: 'dockerHubPwd')]) {
             sh "docker login -u berkansasmaz -p ${dockerHubPwd}"
        }
        
        sh 'docker push berkansasmaz/bestcloudforme-internship-application'
      } 
}