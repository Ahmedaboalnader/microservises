pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                // خطوات البناء هنا
            }
        }
    }
    post {
        success {
            mail to: 'ahmed.mostafa.aboalnader@gmail.com',
                 subject: "Build Successful: ${currentBuild.fullDisplayName}",
                 body: "The build ${currentBuild.fullDisplayName} completed successfully."
        }
        failure {
            mail to: 'ahmed.mostafa.aboalnader@gmail.com',
                 subject: "Build Failed: ${currentBuild.fullDisplayName}",
                 body: "The build ${currentBuild.fullDisplayName} failed."
        }
    }
}
