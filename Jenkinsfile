node('gol')
{
    properties([pipelineTriggers([cron('* * * * 1-5')])])
    stage('VCM'){
        git url: 'https://github.com/badaltechiepi/game-of-life.git',
        branch: 'scripted'
    }
    stage('build'){
        sh 'mvn clean package'
    }
    stage('testreport')
    {
        junit testResults: 'gameoflife-web/target/surefire-reports/*.xml'
    }
    stage('artifectarvhice')
    {
        archiveArtifacts artifacts: 'gameoflife-web/target/*.war'
    }
}