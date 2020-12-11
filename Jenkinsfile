pipeline {
	agent any
	stages {
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
		stage('Jar') {
			steps {
				sh './mvnw clean package -e'
			}
		}
		stage('Sonar') {
			steps {
				withSonarQubeEnv( installationName: 'sonar') { // You can override the credential to be used
					sh  './mvnw org.sonarsource.scanner.maven:sonar-maven-plugin:3.7.0.1746:sonar'
				}
			}
		}
		stage('Upload Nexus') {
			steps {
				nexusPublisher nexusInstanceId: 'nexus', nexusRepositoryId: 'test-nexus', packages: [[$class: 'MavenPackage', mavenAssetList: [[classifier: '', extension: 'jar', filePath: '/Users/selyt2020/Documents/GitHub/ejemplo-maven/build/DevOpsUsach2020-0.0.1.jar']], mavenCoordinate: [artifactId: 'DevOpsUsach2020', groupId: 'com.devopsusach2020', packaging: 'jar', version: '0.0.1']]]
			}
		}
	}
}