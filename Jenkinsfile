pipeline {
	agent any
	environment{
		DOTNET_HOME = "C:\\Program Files\\dotnet"
	}

	stages {
		stage('Checkout'){
			steps {
				git 'https://github.com/RPrezhdarova/House-Renting-System-App'
				}
		}
		stage('Respore Nuget Packeges') {
			steps {
				sh 'dotnet restore HouseRentingSystem.sln'
			}
		}

		stage('Build Project'){
			steps {
				sh 'dotnet build HouseRentingSystem.sln --configuration Release'
			}
		}
		stage ('Run Tests'){
			steps {
				sh 'dotnet test HouseRentingSystem.sln --configuration Release --no-build --verbosity normal'
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