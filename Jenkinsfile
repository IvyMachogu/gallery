pipeline{
    agent any
    
   tools {
       
        nodejs 'Node'
    }
    stages{
        stage('clone code'){
           steps{
               git branch: 'master', url: 'https://github.com/IvyMachogu/gallery.git'
           }
    }
    stage('Build'){
        steps{
            sh 'npm install'
        }
        
       }
    }
}
