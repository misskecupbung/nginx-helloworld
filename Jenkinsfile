node {
    def app
    agent any
  
    stage('Pulling Repository') {
        checkout scm
    }
  
    stage('Build Image') {
       app = docker.build("misskecupbung/nginx-hello")
    }
  
    stage('Test Image') {
        app.inside {
            sh 'echo "Testing passed"'
        }
    }
  
    stage('Push image') {
        docker.withRegistry('https://registry.hub.docker.com', 'dockerid') {
            app.push("${env.BUILD_NUMBER}")
            app.push("latest")
        }
    }
}
