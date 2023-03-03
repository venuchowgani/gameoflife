pipeline{
    agent { label '' }
    stages{
        stage('vcs'){
            steps{
                git url: 'https://github.com/wakaleo/game-of-life.git'
                    branch: 'master'
            }
        }
        stage('package'){
            steps{
                sh 'mvn package'
            }
        }
        stage('post build'){
            steps{
                archiveArtifacts artifacts: '**/target/game-of-life.war',
                                 onlyIfSuccessful: true
                junit testResults: '**/surefire-reports/TEST-*.xml'
            }
        }
    }
}