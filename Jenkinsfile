pipeline {
    agent any
	
	tools {
    jdk 'java 1.8'

  }

    stages {
        stage('CLONE SCM') {
            steps {
                echo 'Cloning GOOGLE HOME PAGE project code'
				git branch: 'main', url: 'https://github.com/Ramakrishnaa007/ramakrishna-mindcircuit13.git'
            }
        }
		
		stage('SONARQUBE ANALYSIS') {
            steps {
                echo 'code inspection of  GAME OF LIFE project code'
			    sh 'mvn clean compile sonar:sonar'
			    
            }
        }
		
		
		stage('Build Artifact ') {
            steps {
                echo 'generating artifact with maven build tool'
				sh 'mvn  install'
            }
        }
		
		stage('Deploy to tomcat') {
            steps {
                echo 'Deploying artifact to tomcat webserver '
				deploy adapters: [tomcat9(credentialsId: 'tomcat-credentials', path: '', url: 'http://52.87.153.78:8081/')], contextPath: 'gameoflife', war: '**/*.war'
            }
        }
    }
}
