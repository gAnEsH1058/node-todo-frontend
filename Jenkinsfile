node {
    
	

    env.AWS_ECR_LOGIN=true
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
	stage('Building image') {
       docker.withRegistry('https://index.docker.io/v1/', 'dockerhub') {
		    def buildName = moregane + ":$BUILD_NUMBER"
			newApp = docker.build buildName
			newApp.push()
        }
	}
	stage('Registring image') {
        docker.withRegistry('https://index.docker.io/v1/', 'dockerhub') {
    		newApp.push 'latest2'
        }
	}
    stage('Removing image') {
        sh "docker rmi $registry:$BUILD_NUMBER"
        sh "docker rmi $registry:latest"
    }
    
}
