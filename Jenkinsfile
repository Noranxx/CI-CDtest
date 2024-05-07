pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Checkout source code from Git
                git branch: 'main', url: 'https://github.com/Noranxx/git-fetch.git'
            }
        }

        stage('Build') {
            steps {
                // Build and package the application using Maven
                sh 'mvn clean package'
            }
        }

        stage('Deploy to Tomcat') {
            environment {
                TOMCAT_URL = '192.168.203.149:8080'  // Replace 'tomcat-host' with your Tomcat host URL
            }
            steps {
                // Copy the WAR file to the running Tomcat container
                sh "curl -T target/my-app.war ${TOMCAT_URL}/manager/text/deploy?path=/my-app&update=true --user noran:123"
            }
        }
    }
}
