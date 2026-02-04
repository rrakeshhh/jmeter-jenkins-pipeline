pipeline {
    agent any

    environment {
        JMETER_HOME = "E:\JMETER\apache-jmeter-5.6.2\"
    }

    stages {
        stage('Checkout') {
            steps {
                echo 'Code checked out from Git'
            }
        }

        stage('Run JMeter Test') {
            steps {
                bat """
                %JMETER_HOME%\\bin\\jmeter.bat -n ^
                -t jmeter-tests\\test.jmx ^
                -l results.jtl
                """
            }
        }
    }
}
