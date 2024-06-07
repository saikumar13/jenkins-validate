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
    }
}
