
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
                sh "docker build -t nandireddy123/reddy1:v1 ."


            }
        }
        stage("push to docker hub"){
        steps{
        withCredentials([string(credentialsId: '', variable: 'dockerpwd')]) {
        sh "docker login -u nandireddy123 -p ${dockerpwd}"
        sh "docker push nandireddy123/reddy:v1"      
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
