pipeline {
   agent any
   environment {
	PATH = "/opt/maven/bin:$PATH"
   }
    stages {
       stage("Build") {
	  steps {
		sh 'mvn clean deploy'
          }
       }
     stage('SonarQube analysis') {
        environment {
           scannerHome = tool 'Sonarqube-scanner'
        }
          steps {
            withSonarQubeEnv('Sonarqube-server') {
                 sh "${scannerHome}/bin/sonar-scanner"
             }
          }
       }
   }
}
