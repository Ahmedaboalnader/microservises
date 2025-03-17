// pipeline {
//     agent any
//     stages {
//         stage('Build') {
//             steps {
//                 // خطوات البناء هنا
//             }
//         }
//     }
//     post {
//         success {
//             mail to: 'ahmed.mostafa.aboalnader@gmail.com',
//                  subject: "Build Successful: ${currentBuild.fullDisplayName}",
//                  body: "The build ${currentBuild.fullDisplayName} completed successfully."
//         }
//         failure {
//             mail to: 'ahmed.mostafa.aboalnader@gmail.com',
//                  subject: "Build Failed: ${currentBuild.fullDisplayName}",
//                  body: "The build ${currentBuild.fullDisplayName} failed."
//         }
//     }
// }
pipeline {
    agent any

   pipeline {
    agent any

    environment {
        REGISTRY = "docker.io/ahmedmosatafa22"
        FRONTEND_IMAGE = "my-frontend"
        SERVER_IP = "your-server-ip"
        SSH_USER = "your-ssh-user"
    }

    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'main', url: 'https://github.com/Ahmedaboalnader/microservises'
            }
        }

        stage('Build Frontend Image') {
            steps {
                sh 'docker build -t $REGISTRY/$FRONTEND_IMAGE:latest ./frontend'
            }
        }

        stage('Push Image to Docker Hub') {
            steps {
                sh 'docker login -u ahmedmostafa22 -p Ahmed@1#2$3'
                sh 'docker push $REGISTRY/$FRONTEND_IMAGE:latest'
            }
        }

        stage('Deploy to Server') {
            steps {
                sshagent(['projectssh']) {
                    sh '''
                    ssh $SSH_USER@$SERVER_IP <<EOF
                    docker pull $REGISTRY/$FRONTEND_IMAGE:latest
                    docker stop frontend || true
                    docker rm frontend || true
                    docker run -d -p 80:80 --name frontend $REGISTRY/$FRONTEND_IMAGE:latest
                    EOF
                    '''
                }
            }
        }
    }
}

 post {
        success {
            mail to: 'ahmed.mostafa.aboalnader@gmail.com',
                 subject: "The script has been bolled",
                 body: "The script has been bolled success"
        }
        failure {
            mail to: 'ahmed.mostafa.aboalnader@gmail.com',
                 subject: "failed ",
                 body: "The build failed."
        }
    }
}

