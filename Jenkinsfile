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


       post{
           always{
               echo'slacknotification'
               slackSend(
                   channel:'YourFirstName_IP1',
                   color: COLOR_MAP[currentResult.currentResult],
                   message:"*${currentBuild.currentResult}:* Job &{env.JOB_NAME} \n build  &{env.BUILD_NUMBER} \n more info at :&{env.BUILD_URL"
                   )
           }
         } 
}
