node {

    stage('SCM Checkout'){
        git credentialsId: '2f511eae-b599-4ab9-820a-b0e195a99e2b', url: 'https://github.com/berkansasmaz/bestcloudforme-internship-application'
    }
    
    stage('MVN Package'){
        def mvnHome = tool name: 'maven-3', type: 'maven'
        def mvnCMD = "${mvnHome}/bin/mvn"
        sh label: '', script: "${mvnCMD} clean package"
    }

     stage('Docker Initialize'){
        def dockerHome = tool 'myDocker'
        env.PATH = "${dockerHome}/bin:${env.PATH}"
     }
     
     stage('Docker which'){
        sh 'which docker'
     }

     stage('Docker Build Image'){
        sh 'docker build -t berkansasmaz/bestcloudforme-internship-application .'
     }     
        
      stage('Docker Push Image'){
        withCredentials([string(credentialsId: 'docker-pwd', variable: 'DockerhubPWD')]) {
            sh "docker login -u berkansasmaz -p ${DockerhubPWD}"
        }
        
        sh 'docker push berkansasmaz/bestcloudforme-internship-application'
      } 
}