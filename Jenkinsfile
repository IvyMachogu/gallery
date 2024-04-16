def COLOR_MAP =[
    'FAILURE':'danger',
    'SUCCESS': 'GOOD'
    ]

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

    post {
        success {
            emailext attachLog: true, 
                body:
                    """
                    <p>EXECUTED: Job <b>\'${env.JOB_NAME}:${env.BUILD_NUMBER})\'</b></p>
                    <p>
                    View console output at 
                    "<a href="${env.BUILD_URL}">${env.JOB_NAME}:${env.BUILD_NUMBER}</a>"
                    </p> 
                      <p><i>(Build log is attached.)</i></p>
                    """,
                subject: "Status: 'SUCCESS' -Job \'${env.JOB_NAME}:${env.BUILD_NUMBER}\'", 
                to: 'ivywabosibori@gmail.com'
        }
        failure {
            emailext attachLog: true, 
                body:
                    """
                    <p>EXECUTED: Job <b>\'${env.JOB_NAME}:${env.BUILD_NUMBER})\'</b></p>
                    <p>
                    View console output at 
                    "<a href="${env.BUILD_URL}">${env.JOB_NAME}:${env.BUILD_NUMBER}</a>"
                    </p> 
                      <p><i>(Build log is attached.)</i></p>
                    """,
                subject: "Status: FAILURE -Job \'${env.JOB_NAME}:${env.BUILD_NUMBER}\'", 
                to: 'ivywabosibori@gmail.com'
        }
}
