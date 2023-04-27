pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'mvn clean install'
            }
        }
        stage('OWASP Dependency Check') {
            steps {
                sh '/home/ubuntu/dependency-check/bin/dependency-check.sh \
                    --scan https://github.com/LearnWithAshish/DVWA.git \
                    --format HTML \
                    --project "<DVWA-ASHSIH>" \
                    --out /home/ubuntu/gitleaks/dep-chk.html'
            }
        }
    }
}
