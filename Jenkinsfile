pipeline {
    agent any
    parameters {
        choice(name: 'DOCKER_IMAGE_1', choices: 'raghuramdevopsengineer/node', description: 'Select Docker Image 1')
        string(name: 'DOCKER_IMAGE_1_VERSION', defaultValue: 'latest', description: 'Version for Docker Image 1')
        choice(name: 'DOCKER_IMAGE_2', choices: 'raghuramdevopsengineer/react', description: 'Select Docker Image 2')
        string(name: 'DOCKER_IMAGE_2_VERSION', defaultValue: 'latest', description: 'Version for Docker Image 2')
        string(name: 'ENVIRONMENT', description: 'Target Environment (e.g., dev, staging, production)')
    }

    stages {
        stage('login to Docker Hub') {
            steps {
                script {
                    docker.withRegistry('https://registry.hub.docker.com', 'docker-hub-authtoken') {
                        docker.image("raghuramdevopsengineer/react:${env.BUILD_NUMBER}")
                        docker.image("raghuramdevopsengineer/node:${env.BUILD_NUMBER}")
                    }
                }
            }
        }

        stage('List Docker Images') {
            steps {
                script {
                    def image1 = params.DOCKER_IMAGE_1
                    def version1 = params.DOCKER_IMAGE_1_VERSION
                    def image2 = params.DOCKER_IMAGE_2
                    def version2 = params.DOCKER_IMAGE_2_VERSION
                    def environment = params.ENVIRONMENT

                    echo "Listing Docker Images and Versions for Environment: $environment"
                    echo "Image 1: $image1:$version1"
                    echo "Image 2: $image2:$version2"
                }
            }
        }
       
    }
}