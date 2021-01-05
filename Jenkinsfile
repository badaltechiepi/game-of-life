pipeline{
    agent{
        label "gol"
    }
    stages{
        stage("scm"){
            steps{
                echo "checkout the code from the github"
                git url: 'https://github.com/badaltechiepi/game-of-life.git',
                    branch: 'release-2.0.0'
            }
        }
        stage("trigger build"){
            steps{
                echo "trigger the build using maven"
                sh 'mvn clean package'
                junit testResults: 'gameoflife-web/target/surefire-reports/*.xml'
                archiveArtifacts artifacts: 'gameoflife-web/target/*.war'
            } 
        }
    }
}