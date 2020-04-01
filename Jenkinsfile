node {
    stage('SCM Checkout'){
        git credentialsId: 'github', url: 'https://github.com/berkansasmaz/bestcloudforme-internship-application'
        git (credentialsId: 'github', url: 'https://github.com/berkansasmaz/bestcloudforme-internship-application', branch: 'dev')
    }
    
//      stage('Docker Initialize'){
//             def dockerHome = tool 'myDocker'
//             env.PATH = "${dockerHome}/bin:${env.PATH}"
//      }
    
     stage('Docker Build Image'){
        sh 'docker build -t berkansasmaz/bestcloudforme-internship-application .'
     }        
     
     stage('Docker Push Image'){
        withCredentials([string(credentialsId: 'docker-pwd2', variable: 'dockerHubPwd')]) {
             sh "docker login -u berkansasmaz -p ${dockerHubPwd}"
        }
        sh 'docker push berkansasmaz/bestcloudforme-internship-application'
     } 
      
     stage('Run Container on Dev Server'){
        def dockerStop = 'docker stop bestcloudforme'
        def dockerRun = 'docker run -p 8080:8080 -d --rm --name bestcloudforme berkansasmaz/bestcloudforme-internship-application'
              sh "ssh -i ~/Desktop/berkan.pem  ec2-user@ec2-3-8-56-230.eu-west-2.compute.amazonaws.com ${dockerStop} ${dockerRun}"
     }
}