pipeline

{
    agent any

    environment {
        PATH="/opt/maven/bin:$PATH"
    }

    stages {

        stage('build code')
        {
            steps 
            {
                sh 'mvn clean package -Dmaven.test.skip=true'
            }
        }

        stage('test code') 
        {
            steps
             {
                sh 'mvn clean test surefire-report:report'
            }
        }

        stage('Sonarcube Analyse Code')
        {
            environment

            {

               scannerHome = tool 'sonartool'

            }
            steps
            {

               withSonarQubeEnv('sonarscanner server')
           
               sh  '${scannerHome}/bin/sonar-scanner'
           }
      }
}

}  

