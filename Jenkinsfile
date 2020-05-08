pipeline {
    agent {
        docker {
            image 'katalonstudio/katalon'
            args "-u root"
        }
    }
    stages {
        stage('Test') {
            steps {
                sh 'katalon-execute.sh -browserType="Web Service" -retry=2 -executionProfile="default" -testSuitePath="Test Suites/CreationSuite"  -apiKey="022bae05-8bc0-4964-899e-da781e8f4e8b" -apiKeyOnPremise=""'
            }
        }
   }
    post {
        always {
            archiveArtifacts artifacts: 'report/**/*.*', fingerprint: true
            junit 'report/**/JUnit_Report.xml'
        }
    }
}
