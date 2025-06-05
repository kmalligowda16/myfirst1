# myfirst1
about first git repository
<br>
commited changes
new changes

pipeline {
agent any
stages {
stage('Checkout') { steps {
// Check out code from Git repository
git url: 'https://github.com/sowmyamadhav21/svitmavan.git', branch: 'master'}}
stage('Build') { steps {
// Run Maven build
bat 'mvn clean package'
}
}
}
post {
always {
// Archive test reports
junit '**/target/surefire-reports/*.xml'
}
success {
echo 'Build and tests succeeded!'
}
failure {
echo 'Build or tests failed.'
}
}
}
