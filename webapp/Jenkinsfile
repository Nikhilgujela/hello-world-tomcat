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
        
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }
        
        stage('Deploy to Tomcat') {
            steps {
               deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: 'tomcatcred', path: '', url: 'http://3.93.10.131:8080/')], contextPath: null, war: '**/*.war'
            }
        }
    }
    
    post {
        success {
            echo 'Deployment successful!'
        }
        failure {
            echo 'Deployment failed!'
        }
    }
}
