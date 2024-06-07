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
                // Set environment variables from properties
                env.demo = props['demo']
                env.demo2 = props['demo2']
                env.Testing_Sample = props['Testing/Sample/']
				}
            }
        }
          stage('Trigger Jobs') {
            steps {
                def jobsProperties = readProperties file: 'jobs.properties'
                jobsProperties.each { key, value ->
                    if (value == 'Y') {
                        build job: key, wait: true
                    }
                }
            }
        }
    }
}
