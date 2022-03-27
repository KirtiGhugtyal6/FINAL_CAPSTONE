pipeline{
    agent any
    tools { 
        maven 'maven3'
    }
    stages
        stage("Installing node_modules, packing and deployment"){
            stages{
                stage("building docker image"){
                    steps{
                        script{
                            dockerImage = docker.build dockerhub_repo + ":$GIT_COMMIT-build-$BUILD_NUMBER"
                        }
                    }
                }
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


        }
}        
