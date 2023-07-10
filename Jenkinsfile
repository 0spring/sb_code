pipeline {
  agent any
  // any, none, label, node, docker, dockerfile, kubernetes
  tools {
    maven 'my_maven'
  }
  environment {
    gitName = '0spring'
    gitEmail = 'dmswn86155@gmail.com'
    githubCredential = 'git_cre'
<<<<<<< HEAD
    dockerHubRegistry = '10.7.7.10:5000/sbimage'
    githubWeb = 'https://github.com/0spring/sb_code'
=======
    dockerHubRegistry = '10.7.7.10/sbimage'
    githubWeb = 'https://github.com/0spring/sb_code.git'
>>>>>>> d6e2339d5b93203782ed24240ef95d7b978c4704
  }

  stages {
    stage('Checkout Github') {
      steps {
          checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: githubCredential, url: githubWeb]]])
          }
      post {
        failure {
          echo 'Repository clone failure'
        }
        success {
          echo 'Repository clone success'  
        }
      }
    }

<<<<<<< HEAD
    stage('Maven Build') {
      steps {
          sh 'mvn clean install'
      }
      post {
        failure {
          echo 'Maven jar build failure'
        }
        success {
          echo 'Maven jar build success'  
        }
      }
    }

    stage('Docker Image Build') {
      steps {
          sh "docker build -t ${dockerHubRegistry}:${currentBuild.number} ."
          sh "docker build -t ${dockerHubRegistry}:latest ."
          }
      post {
        failure {
          echo 'Docker image build failure'
        }
        success {
          echo 'Docker image build success'  
        }
      }
    }
    
    stage('Docker Image Push') {
      steps {
          
          
            sh "docker push ${dockerHubRegistry}:${currentBuild.number}"
            sh "docker push ${dockerHubRegistry}:latest"
      }  
      
      post {
      // docker push가 성공하든 실패하든 로컬의 도커이미지는 삭제.
        failure {
          echo 'Docker Image Push failure'
          sh "docker rmi ${dockerHubRegistry}:${currentBuild.number}"
          sh "docker rmi ${dockerHubRegistry}:latest"
        }
        success {
          echo 'Docker Image Push success'
          sh "docker rmi ${dockerHubRegistry}:${currentBuild.number}"
          sh "docker rmi ${dockerHubRegistry}:latest"
        }
      }
    }


=======
>>>>>>> d6e2339d5b93203782ed24240ef95d7b978c4704
    
  }
}
