node {
    /* Requires the Docker Pipeline plugin to be installed */
    docker.image('maven:3-alpine').inside('-v $HOME/.m2:/root/.m2 --network container:sonarqube') {
        stage('Build') {
            echo 'Building...'
            sh 'mvn --version'
            sh 'mvn -X clean install'
        }
        stage('Scan') {
            echo 'Scanning...'
                sh 'mvn -DskipTests sonar:sonar'
        }
        stage('Test') {
            try {
                echo 'Testing...'
//                sh 'mvn -X test'
            } finally {
                echo 'Testing..Done'
//                archiveArtifcats artifacts: 'build/libs/**/*.jar', fingerprint: true
//                junit 'build/reports/**/*.xml'
            }

        }
        stage('Deploy') {
            echo 'Deploying...'
//            sh 'mvn jar:jar install:install'
//            sh 'java -jar target/demo-0.0.1-SNAPSHOT.jar'
//            sh '.deliver.sh'
        }
    }
}