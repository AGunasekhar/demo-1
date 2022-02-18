node{     
    stage('SCM Checkout'){
        git branch: 'main', credentialsId: 'GitHubCredentials', url: 'https://github.com/AGunasekhar/demo-1.git'  
    }
    
    stage(" Maven Clean Package"){
      sh "mvn clean package"    
    } 
		
    stage('Build Docker Image'){
        sh 'docker build -t guna0501/demo .'
    }
    
    stage('Push Docker Image'){
        withCredentials([string(credentialsId: 'DOKCER_HUB_PASSWORD', variable: 'DOKCER_HUB_PASSWORD')]) {
          bat "docker login -u guna0501 -p ${DOKCER_HUB_PASSWORD}"
        }
        sh 'docker push guna0501/demo'
     }
     
      stage("Deploy To Kuberates Cluster"){
        sh 'kubectl apply -f webapp.yml'
      }  
}
