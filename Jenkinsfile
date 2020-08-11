pipeline {
    agent any
    stages {
        stage('Build Application') {
            steps {
			withMaven(maven : 'apache-maven-3.6.3') {
                bat 'mvn -f pom.xml clean package'
				}
            }
            post {
                success {
                    echo "Now Archiving the Artifacts...."
                    archiveArtifacts artifacts: '**/*.war'
                }
            }
        }
        
     }
}
