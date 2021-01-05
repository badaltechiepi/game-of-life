pipeline{
    agent{
        label "node"
    }
    stages{
        stage('VCM'){
            steps{
                echo "checkout the github repo"
                git url: 'https://github.com/badaltechiepi/game-of-life.git',
                branch: 'declarative'
            }
        stage('build'){
            steps{
                echo "package the build"
                sh 'mvn clean package'
            }
         stage('test report'){
             steps{
                 echo "test report"
                 junit 'gameoflife-web/target/surefire-reports/*.xml'
             }

             }
            

         }   
        }
    }
}