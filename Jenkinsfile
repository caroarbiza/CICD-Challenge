
node {
    stage('Build') {
        checkout scm
        def customImage = docker.build("caroarbiza/cicd-challenge:latest")
        docker.withRegistry('https://registry.hub.docker.com', 'dockerhub') {
        customImage.push("latest")
        }

    }
}



node {
    stage('Deploy') {
        echo 'deploying the application'
        sshagent(credentials: ['SSH-APP']) {
            sh "ssh -o StrictHostKeyChecking=no -l vagrant 192.168.108.210 'sudo docker run -dp 80:3030 caroarbiza/cicd-challenge:latest'"

        }
    }



}
