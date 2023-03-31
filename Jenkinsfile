pipeline {
    agent any
    tools {
        maven "MAVEN3"
	jdk "OracleJDK8"
    }

    environment {
        SNAP_REPO = 'vprofile-snapshot'
        NEXUS_USER = 'admin'
        NEXUS_PASS = 'admin'
        RELEASE_REPO = 'vprofile-release'
        CENTRAL_REPO = 'vpro-maven-central'
        NEXUSIP = '172.31.34.212'
        NEXUSPORT = '8081'
        NEXUS_GRP_REPO = 'vpro-maven-group'
        NEXUS_LOGIN = 'nexuslogin'
    }

    stages{
      
        stage('BUILD'){
	     steps {
	     	  sh 'mvn clean package'
		  sh 'mvn clean install -DskipTests'
	     }

	     post {
	         success {
		      echo 'Now Archiving...'
		      archiveArtifacts artifacts: '**/*.war'
		 }
             }

	}
        
	stage('Unit test'){
	     steps {
	     	 sh 'mvn test'
 	      }
	}
