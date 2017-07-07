node {
    // Mark the code checkout 'stage'....
    stage 'Checkout'
    // Get some code from a GitHub repository.
    git url: 'https://github.com/saucelabs-sample-test-frameworks/Java-TestNG-Selenium.git'
    stage 'Compile'
    bat 'mvn compile'
    stage 'Test'
    sauce('40690117-2c64-4fe8-b826-65e92daf5769') {
        sauceconnect(useGeneratedTunnelIdentifier: true, verboseLogging: true) {
            bat 'mvn test'
        }
    }
    stage 'Collect Results'
    step([$class: 'JUnitResultArchiver', testResults: '**/target/surefire-reports/TEST-*.xml'])
    step([$class: 'SauceOnDemandTestPublisher'])
}
