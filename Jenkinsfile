pipeline {
    agent any
	
	tools {
    jdk 'java 1.8'

  }

    stages {
        stage('CLONE SCM') {
            steps {
                echo 'Cloning GAME OF LIFE project code'
				git branch: 'main', url: 'https://github.com/Ramakrishnaa007/ramakrishna-mindcircuit13.git'
            }
        }
		
		stage('SONARqube ANALYSIS') {
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
				deploy adapters: [tomcat9(credentialsId: 'tomcat-credentials', path: '', url: 'http://ec2-100-26-253-111.compute-1.amazonaws.com:8081/')], contextPath: 'game of life', war: '**/*.war'
            }
        }
    }
}
