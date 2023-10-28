node {
    def scannerHome = tool name: 'sonar', type: 'hudson.plugins.sonar.SonarRunnerInstallation'
    
    stage('BUILD') {
        try {
            // Your existing 'BUILD' stage code
        } catch (Exception e) {
            // Handle exceptions if necessary
            currentBuild.result = 'FAILURE'
            error("Build failed: ${e.message}")
        }
    }

    stage('UNIT TEST') {
        try {
            // Your existing 'UNIT TEST' stage code
        } catch (Exception e) {
            // Handle exceptions if necessary
            currentBuild.result = 'FAILURE'
            error("Unit tests failed: ${e.message}")
        }
    }

    stage('INTEGRATION TEST') {
        try {
            // Your existing 'INTEGRATION TEST' stage code
        } catch (Exception e) {
            // Handle exceptions if necessary
            currentBuild.result = 'FAILURE'
            error("Integration tests failed: ${e.message}")
        }
    }

    stage('CODE ANALYSIS WITH CHECKSTYLE') {
        try {
            // Your existing 'CODE ANALYSIS WITH CHECKSTYLE' stage code
        } catch (Exception e) {
            // Handle exceptions if necessary
            currentBuild.result = 'FAILURE'
            error("Code analysis with Checkstyle failed: ${e.message}")
        }
    }

    stage('SonarQube analysis') {
        try {
            withSonarQubeEnv('sonar') {
                sh "${scannerHome}/bin/sonar-scanner -Dsonar.projectKey=admin"
            }
            timeout(time: 10, unit: 'MINUTES') {
                waitForQualityGate abortPipeline: true
            }
        } catch (Exception e) {
            // Handle exceptions if necessary
            currentBuild.result = 'FAILURE'
            error("SonarQube analysis failed: ${e.message}")
        }
    }

    stage("Publish to Nexus Repository Manager") {
        try {
            // Your existing 'Publish to Nexus Repository Manager' stage code
        } catch (Exception e) {
            // Handle exceptions if necessary
            currentBuild.result = 'FAILURE'
            error("Publish to Nexus Repository Manager failed: ${e.message}")
        }
    }
}
