// example Jenkinsfile for Polaris scans using the Black Duck Security Scan Plugin
// https://plugins.jenkins.io/blackduck-security-scan
pipeline {
    agent any
    stages {
        stage('Polaris') {
		
		
            steps {
			withCredentials([string(credentialsId: 'polaris_token', variable: 'POLARIS_API_TOKEN')]) {
				sh 'whoami'
                security_scan product: 'polaris',
                    polaris_assessment_types: 'SAST',
					polaris_assessment_mode: 'SOURCE_UPLOAD',
                    polaris_application_name: 'hello-java',
                    polaris_project_name: 'hello-java',
					polaris_access_token: "${POLARIS_API_TOKEN}",
					polaris_branch_name: 'main',
                    mark_build_status: 'UNSTABLE',
                    include_diagnostics: false
            } // with Cred
			} 
        }
    }

    post {
        always {
            cleanWs()
        }
    }
}
