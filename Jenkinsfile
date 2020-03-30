node {

    stage('SCM Checkout'){
        git credentialsId: 'github', url: 'https://github.com/berkansasmaz/bestcloudforme-internship-application'
        git (credentialsId: 'github', url: 'https://github.com/berkansasmaz/bestcloudforme-internship-application', branch: 'dev')
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
      
      stage('Run Container on Dev Server'){
        def dockerRun = 'docker run -p 8000:8080 -d --name bestcloudforme berkansasmaz/bestcloudforme-internship-application'
          sshagent(['azure-bestcloudforme']) {
              sh "ssh -o StrictHostKeyChecking=no berkansasmaz@13.89.57.174 ${dockerRun}"
          }

      }
}