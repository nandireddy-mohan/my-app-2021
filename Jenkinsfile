
pipeline{
    agent any
    stages{
        stage('Maven Build'){
            steps{
                sh "mvn clean package"

            }

        }
        stage('Docker Build Image'){
            steps{
                sh "docker build -t nandireddy123/myweb:v1 ."


            }
        }
        stage("push to docker hub"){
        steps{
      withCredentials([string(credentialsId: '', variable: 'dockerPwd')]) {
         sh "docker login -u nandireddy123 -p ${dockerPwd}"
        sh "docker push nandireddy123/myweb:v1"      
      }
            }
        }

        stage("dev -deploy"){
            steps{
                echo "deplot to dev"
            }
        }
      
        
    }
}
