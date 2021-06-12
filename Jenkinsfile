
pipeline{
    agent any
    stages{
        stage('Maven Build'){
            steps{
                echo "${getLatestCommitId()}"
                sh "mvn clean package"

            }

        }
        stage('Docker Build Image'){
            steps{
                sh "docker build . -t mohanwebapp/myweb:${getLatestCommitId()} "


            }
        }
        stage("push to docker hub"){
        steps{
         withCredentials([string(credentialsId: 'Docker -Hub', variable: 'dockerpwd')]) {
         sh "docker login -u mohanwebapp -p ${dockerpwd}"
        sh "docker push mohanwebapp/myweb:${getLatestCommitId()}"      
      }
            }
        }

        stage("dev -deploy"){
            steps{
                sshagent(['docker-dev']){
                    sh "ssh -o StrictHostKeyChecking=no ec2-user@3.25.223.70  docker rm -f myweb"
                    sh "ssh -o StrictHostKeyChecking=no ec2-user@3.25.223.70 docker run -d -p 8080:8080 --name reddy mohanwebapp:${getLatestCommitId()}"
                }
            }
        }
      
        
    }
}
 def getLatestCommitId(){
       def commitId =sh returnStdout: true, script: 'git rev-parse --short HEAD '
       return commitId
 }
