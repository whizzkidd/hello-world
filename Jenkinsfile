pipeline {
	agent any
    stages {
        stage('Build') {
            steps {
                sh 'mvn -B -DskipTests clean package'
            }
        }
        stage('Test') { 
            steps {
                sh 'mvn test' 
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml' 
                }
            }
        }
        stage('Deliver') { 
            steps {
                sh 'java -jar /var/lib/jenkins/workspace/simple-java-maven-app/target/hello-world-1.0.0.jar' 
            }
        }
    }
}
