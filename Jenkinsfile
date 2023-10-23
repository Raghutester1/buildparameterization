pipeline {
    agent any
    parameters {
        choice(name: 'DOCKER_IMAGES', choices: 'raghuramdevopsenginner/react\nraghuramdevopsenginner/node\nraghuramdevopsenginner/fastapi')
        choice(name: 'DOCKER_IMAGES_VERSION', choices: '13\n12\n11\n10\n9\nlatest')
        choice(name: 'ENVIRONMENT', choices: ['DEV','STAGE','PROD'])
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
                }
            }
        }
       
    }
}