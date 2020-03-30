node{
    stage('Scm Checkout'){
    git credentialsId: 'git', url: 'https://github.com/kishanpeddaboina/Docker'
}
    stage('Mvn Package'){
    def mvnHome = tool name: 'maven', type: 'maven'
def mvnCMD = "${mvnHome}/bin/mvn"
    sh "${mvnCMD} clean package"
}
     stage('Build Docker'){
     sh 'docker build -t kishanpeddaboina/my-app:${BUILD_NUMBER} .'
}
    stage('Push Docker Image'){
    withCredentials([string(credentialsId: 'docker', variable: 'docker')]) {
     sh "docker login -u kishanpeddaboina -p ${docker}"
}
     sh 'docker push kishanpeddaboina/my-app:${BUILD_NUMBER}'
  

}




}
