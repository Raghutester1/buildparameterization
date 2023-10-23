pipeline {
    agent any
    parameters {
        choice(name: 'DOCKER_IMAGE_1', choices: 'raghuramdevopsengineer/node\nraghuramdevopsengineer/react\nraghuramdevopsengineer/fastapi', description: 'Select Docker Image 1')
        string(name: 'DOCKER_IMAGE_1_VERSION', choices: 'all', description: 'Version for Docker Images')
        string(name: 'ENVIRONMENT', choices:'DEV\nSTAGE\nPROD', description: 'Target Environment (e.g., dev, staging, production)')
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
                    def image1 = params.DOCKER_IMAGE_1s
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