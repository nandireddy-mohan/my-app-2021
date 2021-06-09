
pipeline{
    agent any
    stages{
        stage(mvn build){
            steps{
                echo "mvn clean package"

            }

        }
        stage(upload to nexus){
            steps{
                     nexusArtifactUploader artifacts: [[artifactId: 'myweb', classifier: '', file: 'target/myweb', type: 'war']],
                     credentialsId: 'nexus3',
                     groupId: 'in.javahome',
                     nexusUrl: '13.211.131.92:8081',
                     nexusVersion: 'nexus3',
                     protocol: 'http',
                      repository: 'Mohan-release',
                       version: '0.0.1'
            }
        }
    }
}
