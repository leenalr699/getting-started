pipeline {
    options {
        timeout(time: 1, unit: 'HOURS')
    }
    
    agent any
    stages {
        
        stage('build and push') {
            
           steps {

             sh "docker build -t docker/getting-started ."
               // This change is done just for make the pipeline fail
             // sh "docker tag docker/getting-started leenalr/docker-study:v1"
             script {
                 
               docker.withRegistry("",'registryCredential') {
                   
                  sh "docker push leenalr/docker-study:v1"
                }
             }
           }
        }
    }
    post {
        
        failure {
            echo 'sending email notification from jenkins'
            
            step([$class: 'Mailer',
      notifyEveryUnstableBuild: true,
      recipients: emailextrecipients([[$class: 'CulpritsRecipientProvider'],
                                      [$class: 'RequesterRecipientProvider']])])

            
       }
    }
}
