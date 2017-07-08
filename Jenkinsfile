pipeline {
    agent any
    // Mark the code checkout 'stage'....
    stages{
        stage ('Checkout'){
    // Get some code from a GitHub repository.
            step{
                git url: 'https://github.com/saucelabs-sample-test-frameworks/Java-TestNG-Selenium.git'
            }
        }        
        stage ('Compile'){
            step{
                bat 'mvn compile'
            }
        }
        stage ('Sauce Connect'){
            step{
                sauce('f98f133d-7705-4698-8f90-25c648c24bcd') {
                     sauceconnect(useGeneratedTunnelIdentifier: true, verboseLogging: true) {
                     }
                }
        }
      }
    stage 'Collect Results'
    step([$class: 'JUnitResultArchiver', testResults: '**/target/surefire-reports/TEST-*.xml'])
    step([$class: 'SauceOnDemandTestPublisher'])
    }       
}
