pipeline{
  agent any

  stages{
    stage('Maven Build'){
      
        branch "develop"
      
      steps{
        sh "mvn clean package"
      }
    }

    stage('Upload To Nexus'){
              branch "develop"
      }
      steps{
        nexusArtifactUploader artifacts:
                 [
                         [artifactId: 'myweb',
                         classifier: '', 
                         file: 'targer/myweb-0.0.1-war',
                         type: 'war']
                         ],
                         credentialsId: 'nexus3', 
                         groupId: 'in.javahome',
                         nexusUrl: 'http://13.211.131.92:8081/', 
                         nexusVersion: 'nexus3',
                         protocol: 'http',
                         repository: 'Mohan-relase', 
                         version: '0.0.1'
        }
    

    
    stage('dev-deploy'){
     
        branch "develop"
      
      steps{
        echo "deploy to dev environment"
      }
    
     }
  }

}
    
