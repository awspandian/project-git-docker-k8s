pipeline {
    agent any
    stages {
        stage('SCM') {
            steps {
               git branch: 'master', url: 'https://github.com/awspandian/project-git-docker-k8s.git'
            }
        }
     	stage('Build') {
            steps {
               sh 'mvn clean'
	           sh 'mvn install'
            }
        }
        stage('Build Docker Image') {

            steps {
                script {
                    app = docker.build("dockerpandian/project")
                    app.inside {
                        sh 'echo $(curl localhost:8080)'
                    }
                }
            }
        }
        stage('Push Docker Image') {

            steps {
                script {
                    docker.withRegistry('https://registry.hub.docker.com', 'docker') {
                        app.push("${env.BUILD_NUMBER}")
                        app.push("latest")
                    }
                }
            }
        }
      stage("Deploy To Kuberates Cluster"){
          sh 'kubectl apply -f sample.yml'
      }
       
    }
}
