pipeline{
	agent {
		label "slave1"
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
		    sh "pwd"
		    sh "ls -la"
		    sh "ls -R"
			
                }
            } 

        }
} 
