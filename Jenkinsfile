pipeline {
    agent any
    stages {
    stage('Install Gitleaks') {
  steps {
    sh '''#!/bin/bash
        curl -LO https://github.com/zricethezav/gitleaks/releases/download/v7.6.0/gitleaks-linux-amd64 && chmod +x gitleaks-linux-amd64 && sudo mv gitleaks-linux-amd64 /usr/local/bin/gitleaks && gitleaks --version
    '''
  }
}
  stage('Run Gitleaks') {
  steps {
    dir('https://github.com/LearnWithAshish/DVWA.git') {
      sh '''#!/bin/bash
          sudo gitleaks detect -f json -r https://github.com/LearnWithAshish/DVWA.git -v --report=/home/ubuntu/gitleaks/gitleaks.json
          exit 0
         '''
        }
    }
  }
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
        sh 'rm -rf dependency-check || true'
        sh 'unzip -qq dependency-check-8.2.1-release.zip'

        // Run Dependency Check on the repository
        sh './dependency-check/bin/dependency-check.sh --scan . --format XML --out dependency-check-report.xml' 
    }
}
}
    }

