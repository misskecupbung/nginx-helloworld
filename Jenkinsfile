node {
    agent any
    
    stage('Pulling Repository') {
        checkout scm
    }
  
    stage('Build Image') {
       docker.build("misskecupbung/nginx-hello")
    }
  
    stage('Test Image') {
            sh 'echo "Testing passed"'
    }
  
    stage('Push image') {
        docker.withRegistry('https://registry.hub.docker.com', 'dockerid') {
            push("${env.BUILD_NUMBER}")
            push("latest")
        }
    }
}
