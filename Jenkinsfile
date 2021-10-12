pipeline {
    agent any

    tools {
        maven 'MavenDefault'
        jdk 'JDKDefault'
    }

    stages {

        stage('Build') {
            steps {
                bat 'mvn clean install sonar:sonar'
            }
        }
        stage('Deploy') {
            steps {

                dir('C:\\Program Files (x86)\\Jenkins\\workspace\\Test-pipeline\\target') {
                }
                bat 'copy target\\helloworld.war "C:\\Program Files\\Apache Software Foundation\\Tomcat 9.0\\webapps"'
                deploy adapters: [tomcat9(credentialsId: '25e89926-a6c1-4c32-b401-2a2f525d7af1', path: '', url: 'http://localhost:8000')], contextPath: 'new', war: '**/*.war'
            }
        }

    }
}
