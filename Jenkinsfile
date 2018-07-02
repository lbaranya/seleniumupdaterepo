pipeline {

    stages {
    
        stage('Download new Version') {
        
            steps {
            
                wget -P /opt/Jenkins/seleniumHub/ $VersionDownloadURL
            
            }        
        
        }
        
        stage('Remove currect version') {
        
            echo 'removing current version'
        
        }        
        
        stage('Deploy new version') {
        
            echo 'Deployinf new version'
        
        }
        
        stage('Test') {
        
            echo 'testing new version'
        
        }
    
    
    }


}
