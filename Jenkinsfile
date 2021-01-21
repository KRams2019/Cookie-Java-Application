node {
 try  {
 notify('Job Started') 

     
  stage('Git-Checkout') {
  git branch: 'master', credentialsId: '01-git', url: 'https://github.com/KRams2019/Cookie-API-Application.git'
  }
 
 def project_path="Cookie-Api-Project/"
 
 dir(project_path) {
    
  stage('Maven-Clean') {
   sh  'mvn clean'
  }
    
 stage('Maven-Compile') {
   sh 'mvn compile'
  }
  
   stage('Maven-Package') {
   sh  'mvn package'
  }
  
   stage('Archive-Artifacts') {
   archiveArtifacts 'target/*.jar'
  }
   
   stage('Terraform Stage'){
   sh 'terraform  init'
   sh 'terraform  apply -auto-approve'
   }
}

notify('Job Completed')   
} catch (err) {
  notify("Error ${err}")
  currentBuild.result = 'FAILURE'
}
}

def notify(status){
    
	}
