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
         stage('SONAR SCANNER') {
            environment {
            sonar_token = credentials('sonartoken')
            }
            steps {
                sh 'mvn sonar:sonar -Dsonar.projectName=$JOB_NAME \
                    -Dsonar.projectKey=$JOB_NAME \
                    -Dsonar.host.url=http://44.208.25.248:9000 \
                    -Dsonar.token=$sonar_token'
            }
        } 
    }
}
