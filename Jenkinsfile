node {
    stage('Build') {
        echo 'Building...'
    }
    stage('Scan') {
        echo 'Scanning...'
        try {
            sh 'mvn -DskipTests clean install sonar:sonar'
            sh 'make check'
        }
        finally {
            junit 'target/surefire-reports/*.xml'
        }
    }
    stage('Test') {
        echo 'Building...'
    }
    stage('Deploy') {
        echo 'Deploying...'
        sh 'deliver.sh'
    }
}