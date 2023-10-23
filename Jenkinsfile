pipeline {
    agent any
    parameters {
        choice(name: 'DOCKER_IMAGES', choices: 'raghuramdevopsengineer/node\nraghuramdevopsengineer/react\nraghuramdevopsengineer/fastapi', description: 'Select Docker Image 1')
        choice(name: 'DOCKER_IMAGES_VERSION', choices: ['all'], description: 'Version for Docker Images')
        choice(name: 'ENVIRONMENT', choices: ['DEV','STAGE','PROD'], description: 'Target Environment (e.g., dev, staging, production)')
    }

    stages {
        stage('login to Docker Hub') {
            steps {
                script {
                    docker.withRegistry('https://registry.hub.docker.com', 'docker-hub-authtoken') {
                    }
                }
            }
        }

        stage('List Docker Images') {
            steps {
                script {
                    def image1 = params.DOCKER_IMAGES
                    def version1 = params.DOCKER_IMAGES_VERSION
                    def environment = params.ENVIRONMENT

                    echo "Listing Docker Images and Versions for Environment: $environment"
                    echo "selected image: $image1:$version1"
                    echo "selected env: $environment"
                }
            }
        }
       
    }
}