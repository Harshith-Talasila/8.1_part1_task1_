pipeline {
  agent any
  triggers { pollSCM('* * * * *') }

  stages {
    stage('Build') {
      steps { echo 'Task: Build the code. Tool: Maven/Gradle/NPM.' }
    }
    stage('Unit and Integration Tests') {
      steps { echo 'Task: Run unit & integration tests. Tools: JUnit, pytest, Jest.' }
    }
    stage('Code Analysis') {
      steps { echo 'Task: Static code analysis. Tools: SonarQube/SonarCloud, ESLint/Flake8.' }
    }
    stage('Security Scan') {
      steps { echo 'Task: Dependency/SAST scan. Tools: npm audit, OWASP Dependency-Check, Snyk.' }
    }
    stage('Deploy to Staging') {
      steps { echo 'Task: Deploy to staging (e.g., AWS EC2). Tools: SSH/rsync/AWS CLI.' }
    }
    stage('Integration Tests on Staging') {
      steps { echo 'Task: Integration tests on staging. Tools: Postman/Newman, pytest.' }
    }
    stage('Deploy to Production') {
      steps { echo 'Task: Deploy to production. Tools: AWS CLI/GitHub Releases.' }
    }
  }
}