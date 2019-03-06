pipeline {
    agent any
    
    stages {
        stage('Prepare') {
            steps {
                sh "echo Prepare..."

            }
        }

        stage('SonarQube analysis') {
            // requires SonarQube Scanner 2.8+
            //def scannerHome = tool 'SonarQube Scanner 3.3';
            withSonarQubeEnv('My SonarQube Server') {
                //sh "${scannerHome}/bin/sonar-scanner"
                sh "/var/jenkins_home/tools/hudson.plugins.sonar.SonarRunnerInstallation/sonar-scanner/bin/sonar-scanner"
            }
        }

        // No need to occupy a node
        stage("Quality Gate"){
            timeout(time: 1, unit: 'HOURS') { // Just in case something goes wrong, pipeline will be killed after a timeout
                def qg = waitForQualityGate() // Reuse taskId previously collected by withSonarQubeEnv
                if (qg.status != 'OK') {
                    error "Pipeline aborted due to quality gate failure: ${qg.status}"
                }
             }
        }
    }
}