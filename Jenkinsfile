pipeline {
  agent none
  stages {
    stage('build') {
      agent {
        docker {
          image 'maven:3.6.3-jdk-11-slim'
        }

      }
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

    stage('package&test') {
      when {
        branch 'master'
      }
      parallel {
        stage('package') {
          steps {
            echo 'step 3'
            sh 'mvn package -DskipTests'
          }
        }

        stage('test1') {
          steps {
            sleep 2
          }
        }

        stage('test2') {
          steps {
            sleep 2
          }
        }

      }
    }

    stage('archive') {
      when {
        branch 'master'
      }
      steps {
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