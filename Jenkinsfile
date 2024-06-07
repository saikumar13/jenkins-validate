pipeline {
    agent any
    stages {
        stage('Load Properties') {
            steps {
				script{
                // Load properties from file
                def props = readProperties file: 'jobs.properties'
                // Print out the properties
                println "Loaded properties: ${props}"       
		}
            }
        }
        stage('Example') {
            steps {
                // Use the environment variables
                sh "echo ${env.demo}"
                sh "echo ${env.demo2}"
                sh "echo ${env.Testing_Sample}"
            }
        }
    }
}
