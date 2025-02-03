node{
  stage('gitcheckout')
  {
    git clone 'https://github.com/malurneelima/simple-java-maven-app'
  }
  stage('')
  {
    sh 'mvn clean package'
  }
}
