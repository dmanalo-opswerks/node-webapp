pipeline {
    agent {
        label 'linux-node'
    }

    stages {
        stage('Building') {
            steps {
                script {
                    sh 'cat /root/.npm/_logs/2024-09-23T05_37_05_709Z-debug-0.log'
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
