pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Test') {
            steps {
                sh 'test -f index.html'
                sh 'test -f Dockerfile'
                sh "grep -q 'DevOps CI/CD Mini Project' index.html"
                echo 'All application checks passed'
            }
        }
       stage('Build Package') {
            steps {
                sh 'tar -czf app-package.tar.gz index.html Dockerfile'
                archiveArtifacts artifacts: 'app-package.tar.gz'
                echo 'Application package created successfully'
            }
        }
    }
}
