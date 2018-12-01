properties([pipelineTriggers([githubPush()])])



node('linux') {   
 
  stage('UnitTests') {    
	git 'https://github.com/zhan0042/java-project.git'
	sh 'init ant'
	junit 'reports/result.xml'
	sh 'ant -f test.xml -v'   
	}   
	
  stage('Build') {    
	sh 'ant'   
	sh 'ant -f build.xml -v'
	}   
   
	

}
