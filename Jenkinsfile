pipeline{
  agent any
    environment {
      PATH = "$PATH:/opt/maven/bin"
    }
    
    stages {

        stage('CLEAN WORKSPACE') {
            steps {
                cleanWs()
            }
        }

        stage('CODE CHECKOUT') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/tahatalha/DevopsProject.git']]])
            }
        }
        stage('BUILD') {
            steps {
                sh 'mvn clean install package'
            }
        } 
    }
}
