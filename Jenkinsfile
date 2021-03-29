pipeline {
	
	environment{
		registry = "vidhya3112/devops"
		registryCredentials = 'docker-hub-id'
		dockerImage = ''
	}
	
	
    agent any
	
	stages
	
	{
		
	 
        stage('Build image') {
        /* This builds the actual image */
            
		steps{
		    script{
        dockerImage = docker.build registry +":$BUILD_NUMBER"
            }
	    }
    }

        stage('Push image') {
        /* 
			You would need to first register with DockerHub before you can push images to your account*/
		steps{
			script{
        docker.withRegistry('',registryCredentials) {
            dockerImage.push()
	}
            } 
                echo "Trying to Push Docker Build to DockerHub"
        }
    }
        
      stage('Run container') {
        /* This builds the actual image */
            
		steps{
		    script{
        dockerImage.run("-p 8096:80 --rm --name pipecontainer")
            }
	    }
    } 

        	
		
    }
}
