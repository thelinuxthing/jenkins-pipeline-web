pipeline {
    agent ubuntu
    stages {
        // Stage 9.1 is removed because we are using Pipeline with SCM
        stage('10.2 build html file') {
            steps {
                sh 'ls'
                sh 'rm -f index.html'
                sh 'ls'
                sh 'cat head.txt >  index.html'
                sh 'cat body.txt >> index.html'
                sh 'echo Version: 10.0."$BUILD_NUMBER" >> index.html'
                sh 'cat html-end.txt >> index.html'
                sh 'cat index.html'
            }
        }
        stage('10.3 deploy to vm1.arthar360.de') {
            steps {
                sh 'docker build . --tag web-server-httpd:v1'
                sh 'docker stop web-server-httpd'
                sh 'docker rm web-server-httpd'
                sh 'docker run -d -n web-server-httpd -p 80:80 web-server-httpd:v1'
            }
        }
    }
}
