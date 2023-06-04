pipeline {
  agent any
  tools {
    maven 'MAVEN'
  }
  stages {
    stage("build"){
      steps {
        echo 'building the application.... Dev'
        checkout scmGit(branches: [[name: '*/develop']], extensions: [], userRemoteConfigs: [[credentialsId: 'git', url: 'https://github.com/supun5687/demo.git']])
        sh "mvn -Dmaven.test.failure.ignore=true clean package"
        }
      }
    stage("test"){
      steps {
        echo 'testing the application....Dev '
        }
      }
    stage("deploy"){
      steps {
        echo 'deploying the application....Dev'
        }
      }
    }
    post{
        always {
            junit(
                allowEmptyResults:true,
                testResults:'*test-reports/.xml'
                )
        }
    }
}
