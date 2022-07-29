pipeline {
    agent any

    stages {
        stage('SCM') {
            steps {
                git 'https://github.com/awspandian/project-git-docker-k8s.git'
            }
        }
		stage('BUILD') {
            steps {
                sh 'mvn clean'
				sh 'mvn install'
            }
        }
		stage('Build Docker Image'){
			sh 'docker build -t dockerpandian/project .'
    }
    
    stage('Push Docker Image'){
        withCredentials([string(credentialsId: 'DOKCER_HUB_PASSWORD', variable: 'DOKCER_HUB_PASSWORD')]) {
          sh "docker login -u dockerpandian -p ${sample-docker}"
        }
        sh 'docker push dockerpandian/project'
     }
		     stage("Deploy To Kuberates Cluster"){
				kubernetesDeploy(
				  configs: 'hippo-deploy.yml', 
				  kubeconfigId: 'eks',
				  enableConfigSubstitution: true
        )
     }
	 
	  /**
      stage("Deploy To Kuberates Cluster"){
        sh 'kubectl apply -f hippo-deploy.yml'
      } **/
	  
    }
}
