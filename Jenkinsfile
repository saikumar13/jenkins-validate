pipeline {
    agent any
    stages {
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
