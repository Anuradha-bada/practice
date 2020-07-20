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
                  echo "conditional expression applied"
                  rtUpload (
                    serverId: 'central', // Obtain an Artifactory server instance, defined in Jenkins --> Manage:
                    spec: """{
                            "files": [
                                    {
                                        "pattern": "var/lib/jenkins/workspace/practice/target/*.jar*",
                                        "target": "libs-snapshot-local"
                                    }
                                ]
                            }"""
                        )
            }
        }
    }
}
