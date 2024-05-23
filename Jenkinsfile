pipeline {
    agent any

    stages {
        stage('CLONE SCM') {
            steps {
                echo 'Code clone from github repository'
				git branch: 'main', url: 'https://github.com/Ramakrishnaa007/mindcircuit13.git'
            }
        }
		stage('BUILD ARTIFACT') {
            steps {
                echo 'Generating artifact by maven build tool'
                sh 'mvn clean install'				
            }
        }
		stage('DEPLOY TO TOMCAT') {
            steps {
                echo 'Code deployment to tomcat'
				deploy adapters: [tomcat9(credentialsId: 'tomcat-credentials', path: '', url: 'http://100.26.252.72:8081/')], contextPath: 'facebook-app', war: '**/*.war'
            }
        }
    }
}
