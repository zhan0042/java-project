properties([pipelineTriggers([githubPush()])])



node('linux') {   
 
	
  stage('Build') {    
	sh 'ant'   
	sh 'ant -f build.xml -v'
	}   
   
	

}
