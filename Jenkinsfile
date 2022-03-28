pipeline{
    agent any
     environment{
        dockerhub_repo = "kirtighugtyal/final_capstone"
        dockerhub_creds = 'e9f78131-b451-409e-844d-21da4dd448ed'
        dockerImage = ''
     }
 tools { 
        maven 'maven3'
    }
    stages
       {
            stage("clean")
            {
                steps{
                    sh "mvn clean"
                }
            }
            stage("Build")
            {
                steps{
                    sh "mvn compile"
                }
                
            }
             stage("TEST")
            {
                steps{
                    sh "mvn test"
 
                }
            } 
             stage("package")
            {
                steps{
                    sh "mvn package"
                }
            } 
             stage("building docker image"){
                    steps{
                        script{
                            dockerImage = docker.build dockerhub_repo + ":$GIT_COMMIT-build-$BUILD_NUMBER"
                        }
                       
                     }    
                }
            stage("Pushing the docker image"){
                    steps{
                        script {
                            docker.withRegistry('', dockerhub_creds){
                                dockerImage.push()
                            }
                        }
                    }
                }    
        }
}      
