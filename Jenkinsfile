@Library('piper-lib') _

pipeline {
    agent {
        node {
            label 'master-agent'   // your agent label
            customWorkspace "/home/ubuntu/jenkins-workspace/spring-petclinic"
        }
    }

    stages {
        stage('Cleanup') {
            steps {
                deleteDir()  // ensures the workspace is empty
            }
        }

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build Backend') {
            steps {
                script {
                    mavenBuild script: this
                }
            }
        }
    }
}


