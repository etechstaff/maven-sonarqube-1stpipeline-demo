pipeline {
  agent any
  tools {
    maven 'maven'
  }
  stages{
    stage('1-git-clone'){
      steps{
          checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'github-credentials', url: 'https://github.com/etechstaff/maven-sonarqube-1stpipeline-demo.git']])
      }
    }
    stage('2-cleanws'){
      steps{
        sh 'mvn clean'
      }
    }
    stage('3-mavenbuilds'){
      steps{
        sh 'mvn package'
      }
    }
    stage('4-unittest'){
        steps{
            sh 'mvn test'
        }
    }
    stage('5-code-quality'){
        steps{
       sh 'mvn clean verify sonar:sonar \
  -Dsonar.projectKey=team6-new-project2 \
  -Dsonar.projectName='team6-new-project2' \
  -Dsonar.host.url=http://ec2-100-26-194-101.compute-1.amazonaws.com:9000 \
  -Dsonar.token=sqp_2b6aab50f93d8047437321a0d275d35fb4a94542'
        }
    }
  }
}
