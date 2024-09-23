pipeline {
    agent {
        label 'linux-node'
    }

    stages {
        stage('Building') {
            steps {
                script {
                    sh 'mkdir -p /home/node/app/ && cp /home/dmanalo/workspace/node-app/* /home/node/app/'
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
