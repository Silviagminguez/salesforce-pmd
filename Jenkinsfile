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
    			       echo "Aqui"
    			        bat ('pmd.bat -d C:/Jenkins/workspace/salesforce-pipeline/force-app/main/default/classes -R rulesets/apex/quickstart.xml -f xml -reportfile C:/Jenkins/workspace/salesforce-pipeline/PMDOutput.xml -failOnViolation false')
    			        dir ("C:/Jenkins/workspace/salesforce-pipeline/"){
    			            echo"Cambio directorio"
    			        }
    			   }
    			}
		    }
		    post {
                always {
                    recordIssues(
                            enabledForFailure: true,
                            tool: pmdParser(pattern: 'PMDOutput.xml'),
                            unstableTotalAll: 20,
                            failedTotalAll: 30,
                    )
                }
            }
		}
	}
}

		
	}
}

