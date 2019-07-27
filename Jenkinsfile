pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
                checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/arulelango/SpringExample.git']]])
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
                sh 'java -version'
                sh 'mvn clean install'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
                sh 'java -jar /var/lib/jenkins/workspace/JenkinsPipeline/target/gs-spring-boot-0.1.0.jar'
            }
        }
    }
}
