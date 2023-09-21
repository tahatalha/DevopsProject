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
                git 'https://github.com/tahatalha/DevopsProject.git'
            }
        }
    }
}
