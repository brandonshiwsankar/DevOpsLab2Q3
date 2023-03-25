pipeline {
    agent any
    tools {
        maven "MAVEN3"
    }
    environment
    {
        DOCKERHUB_PWD=credentials('CredentialID_DockerHubPWD')
    }
                       
stages {
    stage("Check out") {
          steps {
              git branch: 'main', url: 'https://github.com/brandonshiwsankar/DevOpsLab2Q3.git'
          }
          
    }
          
          stage("Build maven project") {
              steps { 
                  sh 'mvn clean install'
              }
          }

            stage ("Docker build") {
                steps {
                  script {
                      sh 'docker build -t shiwsankar/lab3:q1 .'
                  }
              }
          }
          
            stage ("Docker Login") {
                steps {
                    script {
                        sh 'docker login -u shiwsankar -p ${DOCKERHUB_PWD}'
                    }
                }
          }

          stage ("Docker push") {
                steps {
                    script {
                        sh 'docker push shiwsankar/lab3:q1'
                    }
                }
          }

          
    
}