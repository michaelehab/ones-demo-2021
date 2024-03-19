pipeline {
    agent any
    tools {
        go 'go-1.21'
    }
    environment {
        GO121MODULE = 'on'
        TAG = "$GIT_COMMIT"
    }
    stages {
        stage('Build') {
            steps {
                sh 'go build -o cmd/creator/creator-demo ./cmd/creator'
                sh 'go build -o cmd/mutator/mutator-demo ./cmd/mutator'
                sh 'go build -o cmd/transitor/transitor-demo ./cmd/transitor'
            }
        }

        stage('Run') {
            steps {
                sh 'cd scripts/bin && ./launch-mqtt.sh'
            }
        }
    }
}