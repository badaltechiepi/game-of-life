node('gol')
{
    
    properties([parameters([choice(choices: ['master', 'scripted', 'declarative'], description: 'choice the branch', name: 'Branch_name'), 
                            string(defaultValue: 'gameoflife-web/target/surefire-reports/*.xml', description: 'test result', name: 'testresult'), 
                            string(defaultValue: 'gameoflife-web/target/*.war', description: 'artifact', name: 'artifact')])])
    stage('VCM'){
        git url: 'https://github.com/badaltechiepi/game-of-life.git',
        branch: "${params.Branch_name}"
    }
    stage('build'){
        sh 'mvn clean package'
    }
    stage('testreport')
    {
        junit testResults: "${params.testresult}"
    }
    stage('artifectarvhice')
    {
        archiveArtifacts artifacts: "${params.artifact}"
    }
}