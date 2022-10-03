pipeline {
    // ① Select a Jenkins slave with Docker capabilities
    agent {
        label 'docker'
    }

    environment {
        PRODUCT = 'ghcli'
        GIT_HOST = 'anjalibansal87'
        GIT_REPO = 'tp'
    }

    options {
//         ansiColor('xterm')
        skipDefaultCheckout()
        buildDiscarder(logRotator(numToKeepStr: '10'))
    }

    stages {
        // ② Checkout the right branch
        stage('Checkout') {
            steps {
                script {
//                     BRANCH_NAME = env.CHANGE_BRANCH ? env.CHANGE_BRANCH : env.BRANCH_NAME
                    BRANCH_NAME = "main"
//                     deleteDir()
                    git url: "https://github.com/anjalibansal87/tp.git", branch: BRANCH_NAME
                }
            }
        }
	// ③ Build a container with the code source of the application
        stage('Build') {
            steps {
                sh "docker build -t ${env.PRODUCT}:py ."
            }
        }
    }
}
