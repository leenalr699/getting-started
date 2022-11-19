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

             withDockerRegistry([url: "https://hub.docker.com/repository/docker/leenalr/docker-study", credentialsId: "dockerhub"]) {
                    sh("docker push docker/getting-started")
                }
            }
        }
    }
}
