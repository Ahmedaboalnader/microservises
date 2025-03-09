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

    stages {
        stage('Hello') {
            steps {
                echo 'Hello, World!'
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

