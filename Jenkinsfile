


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
        withCredentials([string(credentialsId: 'ssh', variable: 'SECRET')]) {
            sh "sshpass -p $SECRET ssh vagrant@192.168.108.210 'sudo docker run -dp 80:3030 caroarbiza/cicd-challenge:latest'"

        }
    }



}
