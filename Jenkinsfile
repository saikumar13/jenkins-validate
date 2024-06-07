pipeline {
    agent any
    stages {
        stage('Load Properties') {
            steps {
                script {
                    // Load properties from file
                    def props = readProperties file: 'jobs.properties'
                    // Print out the properties
                    println "Loaded properties: ${props}"
                }
            }
        }
        stage('Trigger Jobs') {
            steps {
                script {
                    def jobsProperties = readProperties file: 'jobs.properties'
                    jobsProperties.each { key, value ->
                        if (value == 'Y') {
                            println "Building Jenkins Job: ${key}"
                            build job: key, wait: true
                        }
                    }
                }
            }
        }
    }
}
