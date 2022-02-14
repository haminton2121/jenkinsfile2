pipeline {

	agent any

	parameters {
        string(name:'FROM_BUILD', defaultValue: '', description: 'build source')
        choice(name: 'target', choices: ['target1','target2'], description: 'target1 or target2')
		choice(name: 'build', choices: ['build1','build2'], description: 'mode build npm')
    }
    stages {
        stage('Stage1') {
            steps {
				echo "Hello"
				 sh  """
				 if [ ${target_env} == "target2" ]; then
                    echo "hello"
				 else
                    echo "goodbye"
				 fi
                 """
            }
        }
        stage('stage2') {
            steps {
                    echo "hello"
            }
        }
    }
	post {
		always {
			cleanWs()
		}
	}
}