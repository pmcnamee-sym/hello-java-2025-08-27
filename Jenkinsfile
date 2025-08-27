// example Jenkinsfile for Polaris scans using the Black Duck Security Scan Plugin
// https://plugins.jenkins.io/blackduck-security-scan
pipeline {
    agent any
    stages {
        stage('Polaris') {
            steps {
                security_scan product: 'polaris',
                    polaris_assessment_types: 'SAST,SCA',
					polaris_assessment_mode: 'SOURCE_UPLOAD',
                    polaris_application_name: 'hello-java',
                    polaris_project_name: 'hello-java',
                    mark_build_status: 'UNSTABLE',
                    include_diagnostics: false
            }
        }
    }
    post {
        always {
            cleanWs()
        }
    }
}
