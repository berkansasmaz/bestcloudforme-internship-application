node {

    stage('SCM Checkout'){
        git credentialsId: 'github', url: 'https://github.com/berkansasmaz/bestcloudforme-internship-application'
        git (credentialsId: 'github', url: 'https://github.com/berkansasmaz/bestcloudforme-internship-application', branch: 'dev')
    }
    
//In dockerfile 
//     stage('MVN Package'){
//         def mvnHome = tool name: 'maven-3', type: 'maven'
//         def mvnCMD = "${mvnHome}/bin/mvn"
//         sh label: '', script: "${mvnCMD} clean package"
//     }

    stage("setup_env") {
        sh 'apt-get update -y'
        sh 'apt-get install -y'
    }
        
    stage("Fix the permission issue") {
        agent any
        steps {
            sh "sudo chown root:jenkins /run/docker.sock"
        }
    }
    
     stage('Docker Initialize'){
//         sh "sudo chown jenkins: -R \$PWD/"
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