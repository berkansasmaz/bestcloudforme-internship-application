node {

    stage('SCM Checkout'){
        git credentialsId: 'ed29f538-e3c6-4269-8a50-4c8123667874', url: 'https://github.com/berkansasmaz/bestcloudforme-internship-application'
    }
    
        stage('MVN Package'){
            def mvnHome = tool name: 'maven-3', type: 'maven'
            def mvnCMD = "${mvnHome}/bin/mvn"
            sh label: '', script: "${mvnCMD} clean package"
        }

       stage('Docker Build Image'){
            sh 'docker build -t berkansasmaz/bestcloudforme-internship-application .'
        }        
   
}