pipeline {
  agent any
      stages {
        stage('Supprimer le workspace'){
           steps {
                deleteDir()
           }
      }
      stage('Chekout SCM'){
           steps {
               git branch: 'main', credentialsId: 'id-user-github', url: 'https://github.com/medsrc/projet-dev01.git'
           }  
      }
      stage('Build image docker'){
           steps {
             script {
               sh 'docker build -t myimage_nginx .'
               sh 'docker tag  myimage_nginx med:myimage_nginx' 
               } 
     
           }  
      }
   
       stage('Deploiement application'){
           steps {
             script {
               sh 'docker stop monapp01'
               sh 'docker rm monapp01'
               sh 'docker run -d --name monapp01 --hostname monapp01 -p 8098:80 myimage_nginx' 
               sh 'docker exec  monapp "ifconfig"'
             } 
           
      }       
   }
 }
}
  
