pipeline {
    agent any
    stages {
        stage('Build Application') {
            steps {
                bat 'mvn -f pom.xml clean package'
            }
            post {
                success {
                    echo "Now Archiving the Artifacts...."
                    archiveArtifacts artifacts: '**/*.war'
                }
            }
        }
		stage('Deploy in Staging Environment'){
            steps{
                build job: 'Deploy_Package_Application_Env'

            }
            
        }
		 stage('Deploy to Production'){
            steps{
                timeout(time:5, unit:'DAYS'){
                    input message:'Approve PRODUCTION Deployment?'
                }
                build job: 'Deploy_Application_Prod_Env'
            }
		}
     
   }
}
