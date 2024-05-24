pipeline {
    agent any

    stages {
        stage('CLONE SCM') {
            steps {
                echo 'Code clone from github repository'
				git branch: 'main', url: 'https://github.com/Ramakrishnaa007/ramakrishna-mindcircuit13.git'
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
				deploy adapters: [tomcat9(credentialsId: 'f555ba2b-03fa-48e3-b536-b6ba28d889bb', path: '', url: 'http://ec2-100-25-204-178.compute-1.amazonaws.com:8081/')], contextPath: 'ramakrishna', war: '**/*.war'
            }
        }
    }
}
