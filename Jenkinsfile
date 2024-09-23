pipeline {
    agent {
        label 'linux-node'
    }

    stages {
        stage('Building') {
            steps {
                script {
                    git credentialsId: '7de7f8cb-630c-4734-89e9-6703e3f16db8', url: 'https://github.com/dmanalo-opswerks/node-webapp.git'
                    dockerImage = docker.build('my-node-app:3000/latest', './workspace/node-app/')
                    dockerImage.push()
                }
            }
        }
        stage('Deployment') {
            steps {
                script {
                    sh 'docker run --name my-node-app my-node-app:3000/latest'
                }
            }
        }
    }
}
