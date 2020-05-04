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
    
}
