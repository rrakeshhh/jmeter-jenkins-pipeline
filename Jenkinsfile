pipeline {
    agent any

    environment {
        JMETER_HOME = 'E:/JMETER/apache-jmeter-5.6.3'
    }

    stages {

        stage('Verify JMeter') {
            steps {
                bat "\"%JMETER_HOME%/bin/jmeter.bat\" -v"
            }
        }

        stage('Run JMeter Test') {
            steps {
                bat """
                if not exist results mkdir results
                "%JMETER_HOME%/bin/jmeter.bat" -n ^
                -t jmeter-tests/test.jmx ^
                -l results/results.jtl
                """
            }
        }
    }
}
