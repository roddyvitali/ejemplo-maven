pipeline {
	agent any

	stages {
		stage('Init') {
			steps {
				echo 'Loading...!'
			}
		}
		stage('Author') {
			steps {
				echo 'Roddy Vitali!'
				echo 'Diplomado DevOps!'
			}
		}
	    stage('Compile') {
			steps {
				sh './mvnw clean compile -e'
			}
		}
		stage('Test') {
			steps {
				sh './mvnw clean test -e'
			}
		}
		stage('Package') {
			steps {
				sh './mvnw clean package -e'
			}
		}
		stage('SonarQube analysis') {
			steps {
				withSonarQubeEnv( installationName: 'sonar') { // You can override the credential to be used
					sh  './mvnw org.sonarsource.scanner.maven:sonar-maven-plugin:3.7.0.1746:sonar'
				}
			}
		}
	    stage('Run') {
			steps {
				sh 'nohup bash ./mvnw spring-boot:run &'
			}
		}
		stage('Curl') {
			steps {
				sh 'sleep 20'
				sh 'curl -X GET http://localhost:8081/rest/mscovid/test?msg=testing &'
			}
		}
		stage('End') {
			steps {
				echo 'Finish task'
			}
		}
	}
}