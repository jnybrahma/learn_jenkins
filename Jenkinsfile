pipeline {
    agent any
    stages {
        stage('Build Application') {
            steps {
                bat 'mvn pom.xml clean package'
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
