pipeline {
    agent any
    stages {
        stage('Run UTs') { 
            steps {
                sh 'npm test'
            }
        }
        stage('Build, tag and push docker image') {
            steps {
                sh 'docker build -t nodejs-ex .'
                sh 'docker tag nodejs-ex anmolbabu/nodejs-ex:`date +"%m%d%y_%H%M"`.`git log --format="%H" -n 1`'
                sh 'docker login --username anmolbabu --password redhat --email anmolbudugutta@gmail.com'
                sh 'docker push anmolbabu/nodejs-ex'
            }
        }
    }
}