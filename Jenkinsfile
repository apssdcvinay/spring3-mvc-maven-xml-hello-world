/* groovylint-disable-next-line CompileStatic */
pipeline {
    agent any
    stages {
        stage('GitClone') {
            steps {
                git 'https://github.com/apssdcvinay/spring3-mvc-maven-xml-hello-world.git'
            }
        }
        stage('MavenBuild') {
            steps {
                sh 'mvn package'
            }
        }
        stage('TomcatDeploy') {
            steps{
                withCredentials([usernameColonPassword(credentialsId: 'tomcat_credentails', variable: 'Credentails')]) {
             sh "curl -v -u ${Credentails} -T /var/lib/jenkins/workspace/TomcatPipleLine/target/spring3-mvc-maven-xml-hello-world-1.2.war 'http://52.87.166.149:8080/manager/text/deploy?path=/Spring3-mvn'" 
              }
            }
        }
    }
}
