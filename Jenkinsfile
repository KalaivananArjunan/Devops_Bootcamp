node{

    stage('github checkout'){

        git credentialsId: 'github', url: 'https://github.com/KalaivananArjunan/Devops_bootcamp.git'

    }

    stage('maven clean up'){

       def mavenHome = tool name: 'maven3', type: 'maven'

       def mavenCMD = "${mavenHome}/bin/mvn"

       sh "${mavenCMD} clean"

    }

    stage('build, test and package'){

       def mavenHome = tool name: 'maven3', type: 'maven'

       def mavenCMD = "${mavenHome}/bin/mvn"

       sh "${mavenCMD} package"

    }
    
    stage('Docker Image Build'){

       sh 'docker-compose up -d'

    }
    
    stage('Docker image push') {

        withCredentials([string(credentialsId: 'dockerhub', variable: 'dockerHubPwd')]){

            sh "docker login -u kalaivananarjunan -p ${dockerHubPwd}"

        }

        sh 'docker push kalaivananarjunan/devopsbootcamp2020:latest'

    }
    stage('Pull Image') {

        sh 'docker pull kalaivananarjunan/devopsbootcamp2020'

    }
    stage('Container execution') {

        sh 'docker run -d -p 8891:8891 kalaivananarjunan/devopsbootcamp2020'

    }
    
}
