def server_up = false

pipeline {
agent any
environment{
    PMD= 'C:/pmd-bin-6.30.0/bin'
}
	stages{
		stage('PMD') {
		    steps {
    			script{
    			   dir("${PMD}"){
    			     bat ('pmd.bat -d C:/Jenkins/workspace/salesforce-pipeline/force-app/main/default/classes -R rulesets/apex/quickstart.xml -f html -reportfile C:/Jenkins/workspace/salesforce-pipeline/force-app/PMDOutput.html -failOnViolation false ')
    			   }
    			}
		    }
		    post {
                always {
                    recordIssues(
                            enabledForFailure: true,
                            tool: pmdParser(pattern: '**/PMDOutput.html'),
                            unstableTotalAll: 20,
                            failedTotalAll: 30,
                    )
                }
            }
		}
		
	}
}

