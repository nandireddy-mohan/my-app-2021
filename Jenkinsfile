
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
                sh "docker build -t mohanwebapp/myweb:v1 ."


            }
        }
        stage("push to docker hub"){
        steps{
         withCredentials([string(credentialsId: 'Docker -Hub', variable: 'dockerpwd')]) {
         sh "docker login -u mohanwebapp -p ${dockerpwd}"
        sh "docker push mohanwebapp/myweb:v1"      
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
