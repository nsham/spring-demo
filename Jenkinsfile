node {
    sh 'docker network connect sonarnet jenkins-blueocean'
    /* Requires the Docker Pipeline plugin to be installed */
    docker.image('maven:3-alpine').inside('-v $HOME/.m2:/root/.m2') {

        stage('Build') {
            echo 'Building...'
            sh 'mvn --version'
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
}