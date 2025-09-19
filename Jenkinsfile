@Library('piper-lib') _   // use the library name you set in Jenkins Global Libraries

pipeline {
    agent any
    

    stages {
        stage('Cleanup') {
            steps {
                // Deletes everything in the current workspace
                deleteDir()
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
                    // This comes from vars/mavenBuild.groovy in SAP shared lib
                    mavenBuild script: this
                }
            }
        }

        stage('Test Backend') {
            steps {
                script {
                    // Another SAP shared lib step
                    mavenExecuteTests script: this
                }
            }
        }
    }
}
