pipeline {
    agent any

    tools {
        // Install the Maven version configured as "M3" and add it to the path.
        maven "Maven"
    }
        stages {
            stage('checkout') {
            steps {
                // Get some code from a GitHub repository
                checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/Astutepavan/springboot-webapplication-1.git']])
            }   
           }

        stage('Build') {
            steps {

                // Run Maven on a Unix agent.
                sh "mvn -Dmaven.test.failure.ignore=true clean install"

            }
        stage('versioning') {
            steps {

                // Run Maven on a Unix agent.
                sh "/usr/local/bin/aws s3 cp ./target/mavewebappdemo-2.0.0-SNAPSHOT.war s3://test-buck-00038938938"

            }
        }
    }
}
