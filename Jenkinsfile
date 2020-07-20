pipeline {
    agent any
    environment{
        ServerID='central'
    }
    stages {
        stage('Build') {
            steps {
                echo "Building project using maven"
                 sh "mvn -Dmaven.test.failure.ignore=true clean package"
            }
        }
        stage('pushing to artifactory') {
            when {
                anyOf{
                    expression{env.BRANCH_NAME=='master'}
                    expression{env.BRANCH_NAME=='developer'}       
              }
            steps {
                  echo "env.BRANCH_NAME pushing"
                  rtUpload (
                    serverId: ServerID, // Obtain an Artifactory server instance, defined in Jenkins --> Manage:
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
       stage ('Publish build info') {
          steps {
               rtPublishBuildInfo (
                    serverId: ServerID
                )
            }
        }
    }
}
