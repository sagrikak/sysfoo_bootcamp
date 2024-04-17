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
      agent {
        docker {
          image 'maven:3.6.3-jdk-11-slim'
        }

      }
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
          agent {
            docker {
              image 'maven:3.6.3-jdk-11-slim'
            }
          }
          steps {
            echo 'step 3'
            sh 'mvn package -DskipTests'
          }
        }

        stage('test1') {
          agent {
            docker {
              image 'maven:3.6.3-jdk-11-slim'
            }
          }
          steps {
            sleep 2
          }
        }

        stage('test2') {
          agent {
            docker {
              image 'maven:3.6.3-jdk-11-slim'
            }
          }
          steps {
            sleep 2
          }
        }

      }
    }

    stage('archive') {
      agent {
        docker {
          image 'maven:3.6.3-jdk-11-slim'
        }

      }
      when {
        branch 'master'
      }
      steps {
        archiveArtifacts 'target/*.war'
      }
    }

  }
  post {
    always {
      echo 'This pipeline is completed..'
    }

  }
}
