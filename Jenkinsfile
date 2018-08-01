node {
    /* Requires the Docker Pipeline plugin to be installed */
//    docker.image('maven:3-alpine').inside('-v $HOME/.m2:/root/.m2 --net bridge') {
        stage('Build') {
            echo 'Building...'
//            sh 'mvn --version'
        }
        stage('Scan') {
            echo 'Scanning...'
//            try {
//                sh 'mvn -DskipTests clean install sonar:sonar'
////                sh 'make check'
//            }
//            finally {
//                echo 'Reporting...'
////                junit 'target/surefire-reports/*.xml'
//            }
        }
        stage('Test') {
            echo 'Building...'
            try {
                sh 'mvn check'
            }
            finally {
                archiveArtifacts artifacts: 'build/libs/**/*.jar', fingerprint: true
                junit 'build/reports/**/*.xml'
            }
        }
        stage('Deploy') {
            echo 'Deploying...'
            sh 'deliver.sh'
        }
//    }
}