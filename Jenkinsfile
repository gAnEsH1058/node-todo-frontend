node {
    
	

 
    def newApp
    def registry = 'https://index.docker.io/v1/'
    def registryCredential = 'dockerhub'
	
	stage('Git') {
		git 'https://github.com/gAnEsH1058/node-todo-frontend'
	}
	stage('Build') {
		sh 'npm install'
	}
	stage('Test') {
		sh 'npm test'
	}
	 stage('docker build/push') {
     docker.withRegistry('https://index.docker.io/v1/', 'dockerhub') {
           def app = docker.build("moregane/modejs:${commit_id}", '.').push()
    	 } 
 	}
	
  //  stage('Removing image') {
    //    sh "docker rmi $registry:$BUILD_NUMBER"
      //  sh "docker rmi $registry:latest"
    //}
    
}
