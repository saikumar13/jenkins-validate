pipeline {
    agent node
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
                    def jobsToTrigger = []
                    def counter = 0
                    jobsProperties.each { key, value ->
                        if (value == 'Y') {
                            jobsToTrigger.add(key)
                            counter++
                            if (counter == 2 || counter == jobsProperties.size()) {
                                println "Building Jenkins Jobs: ${jobsToTrigger}"
                                jobsToTrigger.each { job ->
                                    build job: job, wait: false
                                }
                                jobsToTrigger = []
                            }
                        }
                    }
                }
            }
        }
    }
}
