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
		stage('List') {
			steps {
				dir('/Users/selyt2020/Documents/GitHub/ejemplo-maven'){
					sh 'ls'
				}
			}
		}
	    stage('Compile') {
			steps {
				dir('/Users/selyt2020/Documents/GitHub/ejemplo-maven'){
					sh './mvnw clean compile -e'
				}
			}
		}
		stage('Test') {
			steps {
				dir('/Users/selyt2020/Documents/GitHub/ejemplo-maven'){
					sh './mvnw clean test -e'
				}
			}
		}
		stage('Package') {
			steps {
				dir('/Users/selyt2020/Documents/GitHub/ejemplo-maven'){
					sh './mvnw clean package -e'
				}
			}
		}
	    stage('Run') {
			steps {
				dir('/Users/selyt2020/Documents/GitHub/ejemplo-maven'){
					sh 'nohup bash ./mvnw spring-boot:run &'
				}
			}
		}
		stage('Curl') {
			steps {
				dir('/Users/selyt2020/Documents/GitHub/ejemplo-maven'){
				    sh 'sleep 20'
					sh 'curl -X GET http://localhost:8081/rest/mscovid/test?msg=testing &'
				}
			}
		}
		stage('End') {
			steps {
				echo 'Finish task'
			}
		}
	}
}