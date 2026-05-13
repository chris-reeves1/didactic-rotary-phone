pipeline{
    agent any
    options{
        timestamps()
        timeout(time: 5, unit: 'MINUTES')
    }
    stages{
        stage("make a directory"){
            options{
                retry(2)
            }
            steps{
            sh "mkdir -p jenkins-test"
            }
        }
        stage("add a file"){
            steps{
                sh "touch jenkins-test/file1.txt"
            }
        }
    }
    post{
        always {
            archiveArtifacts artifacts: 'jenkins-test/file1.txt', allowEmptyArchive: true
        }
    }
}
