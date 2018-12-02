properties([pipelineTriggers([githubPush()])])

node('linux') {   
 
  stage('UnitTests') {    
	git 'https://github.com/zhan0042/java-project.git'
	withCredentials([[$class: 'AmazonWebServicesCredentialsBinding', accessKeyVariable: 'AWS_ACCESS_KEY_ID', credentialsId: '4d7150bb-3fac-444c-8150-b45d9b7c5099', secretKeyVariable: 'AWS_SECRET_ACCESS_KEY']]) {
        // some block
        sh 'aws cloudformation describe-stack-resources --stack-name jenkins --region us-east-1'  
	}
	sh 'ant -buildfile test.xml'
	junit 'reports/result.xml'
	sh 'ant -f test.xml -v'   
	}   
	
  stage('Build') {    
	sh 'ant'   
	sh 'ant -f build.xml -v'
	}   
  
  stage('Deploy') { 
	sh 'copy /workspace/java-pipeline/dist/rectangle-14.jar amazon S3/cf-templates-1pvao47bf1v4p-us-east-1'
  	}
	
}
