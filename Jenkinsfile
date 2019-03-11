
def label = "mypod-${UUID.randomUUID().toString()}"
podTemplate(label: label, containers: [
    containerTemplate(name: 'temp', image: 'woapy/jenkins-slave:latest', ttyEnabled: true, command: 'cat')
  ]) {
    node(label) {
        stage 'first'
        echo 'worked'

        stage 'second'
        echo 'again'
      
        stage('Get a Maven project') {
            git 'https://github.com/jenkinsci/kubernetes-plugin.git'
            container('maven') {
                stage('Build a Maven project') {
                    sh 'mvn -B clean install'
                }
            }
        }

    }
}
