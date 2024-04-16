pipeline {
  agent any
  tools{
      maven 'Maven3.6.3'
  }
  stages{
      stage("build"){
          steps{
              echo 'step 1'
              sh 'mvn complile'
          }
      }
      stage("test"){
          steps{
              echo 'step 2'
              sh 'mvn clean test'
          }
      }
      stage("package"){
          steps{
              echo 'step 3'
              sh 'mvn package -DskipTests'
          }
      }
  }

  post{
    always{
        echo 'This pipeline is completed..'
    }
  }
}
