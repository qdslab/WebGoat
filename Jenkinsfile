pipeline {
   agent any
   stages {
     
      stage('Git Checkout') {
         steps {
            sleep 5
            echo "Git Checkout";
         }
      }
         
      stage('Fortify Static Code Analysis-SAST') {
         steps {
            echo "Fortify Static Code Analysis begins";
            //fortifyClean addJVMOptions: '', buildID: 'webgoat2', logFile: 'E:\\Jenkin Logs', maxHeap: '';
            //fortifyTranslate addJVMOptions: '', buildID: 'webgoat2', excludeList: '', logFile: '', maxHeap: '', projectScanType: fortifyJava(javaAddOptions: '', javaClasspath: 'C:\\openjdk-11+28_windows-x64_bin\\jdk-11', javaSrcFiles: 'C:\\Users\\Administrator\\Downloads\\WebGoat-5.4-OWASP_Standard_Win32\\WebGoat-5.4', javaVersion: '1.8');
            //fortifyScan addJVMOptions: '', addOptions: '', buildID: 'webgoat2', customRulepacks: '', logFile: '', maxHeap: '', resultsFile: 'webgoat2.fpr';
         }
      }
      
      stage('Deploy to Test Environment') {
         steps {
            sleep 5
            echo "Deploy to Test Environment";
         }
      }

      stage('Fortify Dynamic Code Analysis-DAST') {
         steps {
            echo "Fortify Dynamic Code Analysis-DAST";
            
            powershell label: '', returnStatus: true, script: 'Invoke-WebRequest -Method \'Post\' -Uri \'http://192.168.215.134:8083/webinspect/scanner/scans\' -Body \'{"settingsName": "webgoat", "overrides": { "scanName": "Test3"}\' -ContentType \'application/json\'  -UseBasicParsing'
            
         }
      }
      
      stage('RedWolf Load Test') {
         steps {
            sleep 5
            echo "Perform Load Test using RedWolf";
         }
      }
   }
}
