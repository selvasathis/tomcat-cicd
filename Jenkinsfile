pipeline{
    agent any
    environment {
        MAVEN_HOME = tool 'maven'
    } 
    stages {
        stage ('git SCM') {
            steps {
                script {
                    git 'https://github.com/selvasathis/my-app-project.git'
                }
            }
        }
        stage ('mvn package') {
            steps {
                script {
                    sh "${MAVEN_HOME}/bin/mvn clean package"
                }
            }
        }
        stage ('deploy') {
            steps {
                script {
                    deploy adapters: [tomcat8(credentialsId: 'deploy-tomcat', path: '', url: 'http://52.195.221.50:8080/')], contextPath: '/', war: '**/*.war'
                }
            }
        }
    }
}
