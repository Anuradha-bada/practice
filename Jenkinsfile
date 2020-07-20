pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo "Building project using maven"
                 sh "mvn -Dmaven.test.failure.ignore=true clean package"
            }
        }
        stage('pushing to artifactory') {
            when {
                branch 'developer' || 'master'
            }
            steps {
                  echo "conditional expression applied for developer"
            }
        }
    }
}
