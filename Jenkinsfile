pipeline {
    agent any

    stages {
            stage('Checkout') {
                steps {
                    git 'https://github.com/shivaswaroop40/jenkin_deploy.git'
                }
            }
            stage('Build') {
                steps {

                    // Run Maven on a Unix agent.
                    sh "mvn -Dmaven.test.failure.ignore=true clean package"

                    // To run Maven on a Windows agent, use
                    // bat "mvn -Dmaven.test.failure.ignore=true clean package"
            }
            
        }
            stage('Deploy') {
                steps {
                    deploy adapters: [tomcat9(credentialsId: '28236422-e912-4f15-9f3c-e7479fb7287a', path: '', url: 'http://localhost:8081')], contextPath: 'mvnwebapp', war: 'target/mvnwebapp.war'
                }
            }
    }
}
