pipeline {
    agent {
        label 'linux-node'
    }

    stages {
        stage('Building') {
            steps {
                script {
                    dockerImage = docker.build('node-app-image', '/home/dmanalo/workspace/node-app/')
                    dockerImage.push()
                }
            }
        }
        stage('Deployment') {
            steps {
                script {
                    sh 'docker run --name my-node-app -d node-app-image'
                }
            }
        }
    }
}
