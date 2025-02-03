node{
    stage('git')
    {
        git 'https://github.com/malurneelima/simple-java-maven-app.git' 
    }
    stage('compile')
    {
        sh 'mvn clean package'
    }
    stage('email')
    {
        mail bcc: '', body: 'hi hello from jenkins', cc: '', from: '', replyTo: '', subject: 'git status', to: 'neelima.malur@gmail.com'
    }
    stage('sonar')
    {
        withSonarQubeEnv('sonar')
        {
            sh 'mvn sonar:sonar'
        }
    }
    stage('quality gate status check')
    {
        timeout(time: 1, unit: 'HOURS') {
              def qg = waitForQualityGate()
              if (qg.status != 'OK') {
                  error "Pipeline aborted due to quality gate failure: ${qg.status}"
              }
          }
    }
}
