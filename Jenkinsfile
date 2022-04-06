pipeline{
    agent any
    stages{
        stage('Hello'){
            steps{
                echo 'hello this is first stage'
            }
        }
        stage('Test'){
            steps{
                sh 'mvn clean clover:setup test clover:aggregate clover:clover'
            }
        }
        stage('Clover Reports'){
            steps{
                 clover(cloverReportDir: 'target/site', cloverReportFileName: 'clover.xml',
                // optional, default is: method=70, conditional=80, statement=80
                 healthyTarget: [methodCoverage: 70, conditionalCoverage: 80, statementCoverage: 80],
                // optional, default is none
                unhealthyTarget: [methodCoverage: 50, conditionalCoverage: 50, statementCoverage: 50],
                // optional, default is none
                failingTarget: [methodCoverage: 0, conditionalCoverage: 0, statementCoverage: 0]
            )
            }
        }
    }
}