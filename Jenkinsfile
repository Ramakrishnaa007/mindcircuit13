pipeline {
    agent {slave1}

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
				deploy adapters: [tomcat9(credentialsId: 'tomcat-credentials', path: '', url: 'http://ec2-107-23-97-34.compute-1.amazonaws.com:8090/')], contextPath: 'rk-job', war: '**/*.war'
            }
        }
    }
}
