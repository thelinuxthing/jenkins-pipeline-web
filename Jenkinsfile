pipeline {
    agent any
    stages {
        // Stage 9.1 is removed because we are using Pipeline with SCM
        stage('9.2 build html file') {
            steps {
                sh 'ls'
                sh 'rm -f index.html'
                sh 'ls'
                sh 'cat head.txt >  index.html'
                sh 'cat body.txt >> index.html'
                sh 'echo Version: 8.0."$BUILD_NUMBER" >> index.html'
                sh 'cat html-end.txt >> index.html'
                sh 'cat index.html'
            }
        }
        stage('9.3 deploy to vm1.arthar360.de') {
            steps {
                sh 'scp -P 2222 index.html root@vm1.arthar360.de:/var/www/html/jenkins-demo/index.html'
            }
        }
    }
}
