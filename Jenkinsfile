pipeline{
    agent any
     environment{
        dockerhub_repo = "kirtighugtyal/final_capstone"
        dockerhub_creds = 'e9f78131-b451-409e-844d-21da4dd448ed'
        dockerImage = ''
    tools{
        maven'maven3'
    }
    stages{
        stage("Installing node_modules, packing and deployment"){
            when{
                branch 'main'
            }
            stages{
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
                                dockerImage.push('latest')
                                dockerImage.push('v1')
                            }
                        }
                    }
                }
            }
        }
    }
