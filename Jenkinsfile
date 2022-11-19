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

             docker.withRegistry("https://hub.docker.com/repository/docker/leenalr/docker-study",'dockerhub') {
               sh("docker push leenalr/docker-study")
                }
            }
        }
    }
}
