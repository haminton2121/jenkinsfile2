pipeline {

	agent any

	parameters {
        string(name:'FROM_BUILD', defaultValue: '', description: 'build source')
        choice(name: 'target', choices: ['target1','target2'], description: 'target1 or target2')
		choice(name: 'build', choices: ['build1','build2'], description: 'mode build npm')
    }
    stages {
		stage('Set Build Version and Env Variable') {
			steps {
				script {				
				def VERSION = VersionNumber projectStartDate: '2018-08-10', versionNumberString: '${BUILD_YEAR}.${BUILD_MONTH,XX}.${BUILD_DAY,XX}.${BUILD_NUMBER}', versionPrefix: ''
				echo "${VERSION}"
				env.DPLVERSION="${VERSION}"
				currentBuild.displayName = VERSION
                }
            }
        }
        stage('Stage1') {
            steps {
				echo "Hello"
				 sh  """
				 if [ ${target} == "target2" ]; then
                    echo "hello"
				 else
                    echo "goodbye"
				 fi
                 """
            }
        }
        stage('stage2') {
            steps {
                script {
                    build job: "Java_Job", parameters: []
                }
                
            }
        }
    }
	post {
		always {
			cleanWs()
		}
	}
}