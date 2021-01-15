def server_up = false

pipeline {
agent any
	stages{
		stage('PMD') {
		    steps {
			sh 'vendor/bin/phpmd . xml build/phpmd.xml --reportfile **/PDMOutput.xml --exclude vendor/ || exit 0'
			pmd canRunOnFailed: true, pattern: 'build/logs/pmd.xml'
		    }
		}
	}
}
