pipeline {
    options {
        timeout(time: 1, unit: 'HOURS')
    }
    agent {
        label 'ubuntu-1804 && amd64 && docker'
    }
    stages {
        stage('build and push') {
           steps {

             sh "docker build -t docker/getting-started ."
             sh "docker tag docker/getting-started leenalr/docker-study:v1"

             withDockerRegistry([url: "https://hub.docker.com/repository/docker/leenalr/docker-study", credentialsId: "dockerhub"]) {
                    sh("docker push leenalr/docker-study")
                }
            }
        }
    }
}
