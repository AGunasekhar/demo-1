node{     
    stage('SCM Checkout'){
        git branch: 'main', credentialsId: 'git', url: 'https://github.com/AGunasekhar/demo-1.git'  
    }
    
    stage(" Maven Clean Package"){
      sh "mvn clean package"    
    } 
		
    stage('Build Docker Image'){
        sh 'docker build -t guna0501/demo .'
    }
    stage('start application'){
        sh 'docker run -itd --name demoapp -p 8081:8080 guna0501/demo'
    }
}
