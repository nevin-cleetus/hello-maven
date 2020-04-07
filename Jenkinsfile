pipeline {
    
    agent any

    environment
    {        
	registry = "nevincleetus/helloworld-repo"
        registryCredential = 'dockerhub'
        dockerImage = ''  
    }		
    tools { 
        maven 'M2_HOME'         
    }		
    stages {	    
	stage ('Initialize') {
            steps {
                sh '''
                    echo "PATH = ${PATH}"
                    echo "M2_HOME = ${M2_HOME}"
                '''
            }
        }	
	stage ('Build') {
            steps {
                sh 'mvn clean package test'
            }         
        }    
	    
        stage('Building image') {
           steps{
               script {
                   dockerImage = docker.build registry + ":$BUILD_NUMBER"
               }
           }
        }	 
    }	
}
