pipeline {
    agent any
    stages {
    stage('Checkout') {
        // Check out your Git repository
        steps {
        git 'https://github.com/LearnWithAshish/DVWA.git'
    }
    }
    stage('Dependency Check') {
        // Download the Dependency Check CLI
        steps {
        sh 'curl -LO https://github.com/jeremylong/DependencyCheck/releases/download/v8.2.1/dependency-check-8.2.1-release.zip'

        // Unzip the Dependency Check CLI
        sh 'unzip -qq dependency-check-8.2.1-release.zip'

        // Run Dependency Check on the repository
        sh './dependency-check/bin/dependency-check.sh --scan . --format XML --out dependency-check-report.xml'

        // Archive the Dependency Check report as an artifact
        archiveArtifacts artifacts: 'dependency-check-report.xml'
    }

    // Add more stages as needed
}
}
    }

