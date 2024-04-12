pipeline{
    agent {
        node {
            label "maven"
        }
    }
    environment {
         PATH = "/opt/apache-maven-3.9.6/bin:$PATH"
    }
    stages {
        stage('build') {
            steps{
                
                sh 'mvn clean deploy'
               
        }
      }

       stage ("Sonar Analysis") {
            environment {
               scannerHome = tool 'sonar-scanner'
            }
            steps {
                
                withSonarQubeEnv('valaxy-sonarqube-server') {    
                    sh "${scannerHome}/bin/sonar-scanner"
                
                }    
               
            }   
        }
       

      
    }
    }