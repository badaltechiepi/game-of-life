pipeline
{
    agent
    {
        label 'gol'
    }
    triggers{cron('H/30 * * * 1-5')}
    parameters
    {
       string(name: 'testresult', defaultValue: 'gameoflife-web/target/surefire-reports/*.xml', description: 'test result to be shown')
       string(name: 'artifect', defaultValue: 'gameoflife-web/target/*.war', description: 'artifect')
       choice(name: 'branch', choices: ['declarative', 'scripted', 'master'], description: 'githubrepo')
    }
    stages
    {
        stage('VCM')
        {
            steps
            {
                echo "checkout the github repo"
                git url: 'https://github.com/badaltechiepi/game-of-life.git',
                branch: "${params.branch}"
            }
        }
        stage('build')
        {
            steps
            {
                echo "package the build"
                sh 'mvn clean package'
            }
        }
        stage('test report')
        {
            steps
            {
                 echo "test report"
                 junit "${params.testresult}"
             }

        }
        stage('build archive')
        {
            steps
            {
                 echo "archive"
                 archiveArtifacts artifacts: "${params.artifect}"
             }

        }   
    }
}