pipeline {
    options {
        timeout(time: 1, unit: 'HOURS')
    }
    agent any
    stages {
        stage('build and push') {
           steps {

             sh "docker build -t docker/getting-started ."
             sh "docker tag docker/getting-started leenalr/docker-study:v1"
             script {
               docker.withRegistry("",'dockerhub') {
                  sh "docker push leenalr/docker-study"
                }
             }
            }
        }
    }
}
