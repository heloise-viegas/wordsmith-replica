pipeline {
    agent any
    environment
    {
     DOCKERHUB_CREDENTIALS = credentials('Dockerhub')
     IMAGE_TAG = '$BUILD_NUMBER'
    }
    stages {
        
        stage('Clone')
        {
            steps{
                cleanWs()
		          git(
                   url:"https://github.com/heloise-viegas/wordsmith-replica.git",
                   branch:"main"
                  )

 
            }
        }



	    
      
    stage('Push') {
      steps {
        sh 'docker ps'
      }
        post {
          success{
              sh """
                    git clone https://github.com/heloise-viegas/wordsmith-kubernetes-files.git
                    cd ./wordsmith-kubernetes-files/k8s-manifests
	            tag="\$(cat api.yaml | grep "image")"
		          echo $tag
                  
                    
                """
          }  
            

  }
    }
  
        
        
    
    }
}
