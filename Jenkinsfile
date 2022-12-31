node {
    stage('Pull the file off Nexus') {
        withCredentials([usernameColonPassword(credentialsId: 'nexus-for-jenkins', variable: 'NEXUS_CREDENTIALS')]) {
            sh script: 'curl -u ${NEXUS_CREDENTIALS} -o reward-app.jar "http://localhost:8081/repository/maven-snapshots/com/mart/rewards-app/1.0.1-SNAPSHOT/rewards-app-1.0.1-20221229.180623-1.jar"'
        }
    }
stage('Upload file(s) to S3') {
            withAWS(region:'us-east-2',credentials:'aws-for-jenkins') {
                s3Upload(bucket:"learning-jenkins", file:'reward-app.jar');
            }
    }
}