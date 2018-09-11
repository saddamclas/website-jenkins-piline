node {
    def app

    stage('Clone repository') {
        /* Let's make sure we have the repository cloned to our workspace */

        checkout scm
    }

    stage('Build images') {
        /* This builds the actual image; synonymous to
         * docker build on the command line. */
             echo "${env.BUILD_NUMBER}"
             sh 'docker build -t saddamclas/website-test:${env.BUILD_NUMBER} -f website . '
    }
    stage('Push Image') {
            docker.withRegistry('https://registry.hub.docker.com', 'ec6095eb-472e-419b-ad61-8454d3afb61c') {
            echo "${env.BUILD_NUMBER}"
            sh "docker push saddamclas/website-test:${env.BUILD_NUMBER}"
           }
   }
    stage('Deploy ') {  
          /*  sh " docker srevice create --name web -p 9089:80  linuxcloudops/website-test:${env.BUILD_NUMBER}"  */
         }
} 
