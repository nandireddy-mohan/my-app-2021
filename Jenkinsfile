
pipeline{
    agent any
    stages{
        stage('Maven Build'){
            steps{
                sh "mvn clean package"

            }

        }
        stage('upload to nexus'){
            steps{
                     nexusArtifactUploader artifacts: [[artifactId: 'myweb', classifier: '', file: 'myweb-0.0.1-RELEASE.war', type: 'war']],
                     credentialsId: 'nexus3',
                     groupId: 'in.javahome',
                     nexusUrl: '13.211.131.92:8081',
                     nexusVersion: 'nexus3',
                     protocol: 'http',
                      repository: 'Mohan-release',
                       version: '0.0.1-RELEASE'
            }
        }
    }
}
