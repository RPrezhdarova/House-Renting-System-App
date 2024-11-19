pipeline {
	agent any
	environment{
		DOTNET_HOME = "C:\\Program Files\\dotnet"
	}

	stages {
		stage('Checkout'){
			steps {
				checkout scm
				}
		}
		
		stage('Setup .NET'){
			steps {
				bat 'dotnet --version'
				}
		}

		stage('Respore') {
			steps {
				bat 'dotnet restore'
			}
		}

		stage('Build Project'){
			steps {
				bat 'dotnet build --no-respore'
			}
		}
		stage ('Run Tests'){
			steps {
				bat 'dotnet test --no-build --verbosity normal'
			}
		}
	}
	post {
        success {
            echo 'Build and tests completed successfully!'
        }
        failure {
            echo 'Build or tests failed!'
        }
    }
}
