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
               sh 'git clone https://github.com/medsrc/projet-dev01.git'
           }  
    }
  }
}
