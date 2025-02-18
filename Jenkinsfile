pipeline {
  agent { label 'slave2' }	
    stages {
        stage('Checkout') {             
            steps {
                sh "rm -rf dhl"
                sh "git clone https://github.com/basavarajmallad/dhl.git"
				 sh "cd dhl"
            }
        }
		    stage('Set up Environment') {
        steps {
            sh 'export export JAVA_HOME=$(dirname $(dirname $(readlink -f $(which java))))'            
	        sh 'export MAVEN_HOME=/usr/share/maven'           
        }
    }
           stage('build') {             
            steps {               
                sh "mvn clean package"
                  }
        }
 
	 	    	     stage('Run Application') {
            steps {
                echo 'Running Spring Boot application...'
                sh 'mvn spring-boot:run '

            }
        }
    }
}
