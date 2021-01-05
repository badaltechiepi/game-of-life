node('gol')
{
    properties([pipelineTriggers([cron('* * * * 1-5')])])
    stages('VCM'){
        git url: 'https://github.com/badaltechiepi/game-of-life.git',
        branch: 'scripted'
    }
    stages('build'){
        sh 'mvn clean package'
    }
    stages('testreport')
    {
        junit testResults: 'gameoflife-web/target/surefire-reports/*.xml'
    }
    stages('artifectarvhice')
    {
        archiveArtifacts artifacts: 'gameoflife-web/target/*.war'
    }
}