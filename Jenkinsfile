pipeline {    
    agent any
    stages {
        stage('Deploy/Build App') {
            steps {
                sh '''
                    echo 'Application deployed successfully!'
                ''' 
            }
        }
         stage('Frontend tests') {
            steps {
               sh '''
                    echo 'Application deployed successfully!'                
                ''' 
               
            }
        }
         stage('Backend tests') {
            steps {
                  sh '''
                   cd  backend-project/
                   npm run test:report
                
                
                ''' 
            }
        }
         stage('Performance tests') {
            steps {
                sh '''
                    cd performance-tests/
                    rm test1.csv -Rf && rm html-reports/ -Rf
                    jmeter -n -t login-logout.jmx -l test1.csv -e -o html-reports/
                '''
                publishHTML([
                    allowMissing: false, 
                    alwaysLinkToLastBuild: false, 
                    keepAll: false, 
                    reportDir: 'performance-tests/html-reports', 
                    reportFiles: 'index.html', 
                    reportName: 'JMeter dashboard report', 
                    reportTitles: ''
                ])
            }
        }
    }



}


