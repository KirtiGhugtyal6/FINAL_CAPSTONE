pipeline{
    agent any
     environment{
        dockerhub_repo = "kirtighugtyal/final_capstone"
        dockerhub_creds = 'e9f78131-b451-409e-844d-21da4dd448ed'
        dockerImage = ''
        tools { 
        maven 'maven3'
    }
    stages
       {
          stage("Build")
            {
                steps{
                    sh "mvn compile"
                }
                
            }
            stage("Test")
            {
                steps{
                    sh "mvn clean test"
                }
            }
            stage("Package")
            {
                steps{
                    sh "mvn clean package"
                }
            }
      }
}
