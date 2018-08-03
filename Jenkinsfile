node {
    /* Requires the Docker Pipeline plugin to be installed */
    docker.image('maven:3-alpine').inside('-v $HOME/.m2:/root/.m2 --network container:sonarqube') {
        stage('Build') {
            echo 'Building...'
//            sh 'mvn --version'
        }
        stage('Scan') {
            echo 'Scanning...'
                sh 'mvn -DskipTests clean install sonar:sonar'
        }
        stage('Test') {
            try {
                echo 'Testing...'
                junit '**/target/*.xml'
            } catch (err) {
                if (currentBuild.result == 'UNSTABLE' || currentBuild.result == 'FAILURE')
                    throw err
            } finally {
                echo 'Testing..Done'
            }

        }
        stage('Deploy') {
            echo 'Deploying...'
            sh 'deliver.sh'
        }
    }
}