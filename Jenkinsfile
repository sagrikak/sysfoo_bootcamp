pipeline {
  agent any
  stages {
    stage('build') {
      steps {
        echo 'step 1'
        sh 'mvn compile'
      }
    }

    stage('test') {
      steps {
        echo 'step 2'
        sh 'mvn clean test'
      }
    }

    stage('package') {
      steps {
        echo 'step 3'
        sh 'mvn package -DskipTests'
      }
    }

    stage('archive') {
      steps {
        echo 'step 4'
        archiveArtifacts 'target/*.war'
      }
    }

  }
  tools {
    maven 'Maven3.6.3'
  }
  post {
    always {
      echo 'This pipeline is completed..'
    }

  }
}
