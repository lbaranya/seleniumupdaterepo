pipeline {

    agent any

    stages {
    
        stage('Download new Version') {
        
            steps {
            
                sh 'wget -P /opt/Jenkins/seleniumHub/ $VersionDownloadURL'
            
            }        
        
        }
        
        stage('Remove currect version') {
            steps {
        
                sh 'echo "removing current version"'
                sh 'echo "Stoping Selenium HUB"'
                sh 'curl --output /dev/null --silent --head --fail $SELENIUM_BASE_URL$SELENIUM_SHUTDOWN_URL'
                sh 'echo "$OLD_VERSION_PATH$SELENIUM_JAR_NAME"'
                sh 'echo "$SELENIUM_BASE_PATH$SELENIUM_JAR_NAME $OLD_VERSION_PATH$SELENIUM_JAR_NAME"'
                sh 'rm $OLD_VERSION_PATH$SELENIUM_JAR_NAME'
                sh 'mv $SELENIUM_BASE_PATH$SELENIUM_JAR_NAME $OLD_VERSION_PATH$SELENIUM_JAR_NAME'
            }
        }        
        
        stage('Deploy new version') {
        
            steps  {
                sh 'echo "Deployinf new version"'
                sh 'mv $SELENIUM_BASE_PATH*.jar $SELENIUM_BASE_PATH$SELENIUM_JAR_NAME'
                build job:$START_SELENIUM_JOB
            }
        }
        
        stage('Test') {
        
            steps {
                sh 'echo "testing new version"'
                if (sh 'curl --output /dev/null --silent --head --fail $SELENIUM_VERIFICATION_URL') {

                    sh 'echo "Selenium Hub is Up"'

                } else {
                 
                    sh 'echo "Selenium Hub is down"'
                }
            }
        
        }
    
    
    }
    
    environment {
    
        SELENIUM_BASE_URL = 'http://localhost:4444'
        SELENIUM_CHECK_URL = '/grid/console'
        SELENIUM_SHUTDOWN_URL = '/lifecycle-manager/LifecycleServlet?action=shutdown'
        OLD_VERSION_PATH = '/opt/Jenkins/seleniumHub/previousVersion/'
        SELENIUM_JAR_NAME = "selenium-server-standalone.jar"
        SELENIUM_BASE_PATH = '/opt/Jenkins/seleniumHub/'
        START_SELENIUM_JOB = 'SeleniumHubStart'
    }


}
