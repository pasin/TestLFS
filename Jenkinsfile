pipeline {
    agent none
    options {
        timeout(time: 60, unit: 'MINUTES')
    }
    stages {
        stage('Run Tests') {
            parallel {
                stage('macOS') {
                    when {
                        expression { return true } // Skip for now
                    }
                    agent { label 'mob-e2e-mac-01' }
                    steps {
                        echo "Run macOS Test"
                        sh 'which git'
                        sh 'ls -lh dataset/server/dbs'
                        sh 'ls -lh dataset/server/blobs'
                    }
                }
                stage('linux') {
                     when {
                        expression { return true } // Skip for now
                    }
                    agent { label 'mob-e2e-deb-02' }
                    steps {
                        echo "Run linux Test"
                        sh 'which git'
                        sh 'ls -lh dataset/server/dbs'
                        sh 'ls -lh dataset/server/blobs'
                    }
                }
                stage('windows') {
                     when {
                        expression { return false } // Skip for now
                    }
                    agent { label 'mob-e2e-win-01' }
                    steps {
                        echo "Run windows Test"
                        sh 'ls -lh dataset/server/dbs'
                        sh 'ls -lh dataset/server/blobs'
                    }
                }
            }
        }
    }
}