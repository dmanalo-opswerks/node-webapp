pipeline {
    agent {
        label 'linux-node'
    }

    stages {
        stage('Building') {
            steps {
                script {
                    sh 'mkdir -p /home/node/app/ && cp -r /home/dmanalo/workspace/node-app/* /home/node/app/'
                    sh 'pwd'
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
