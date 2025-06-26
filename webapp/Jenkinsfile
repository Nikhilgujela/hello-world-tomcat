pipeline {
    agent any
    
    tools {
        jdk 'jdk21'
        maven 'maven3'
    }

    stages {
        stage('Git Checkout') {
            steps {
                git changelog: false, poll: false, url: 'https://github.com/Nikhilgujela/hello-world-tomcat.git'
            }
        }
        stage('maven build') {
            steps {
                sh "mvn clean package"
            }
        }
    }
}
