pipeline {
    agent any

    environment {
        JMETER_HOME = 'E:\\JMETER\\apache-jmeter-5.6.2'
    }

    stages {

        stage('Verify JMeter') {
            steps {
                bat "\"${JMETER_HOME}\\bin\\jmeter.bat\" -v"
            }
        }

        stage('Run JMeter Tests in Parallel') {
            parallel {

                stage('Login Test') {
                    steps {
                        bat """
                        if not exist results mkdir results
                        "${JMETER_HOME}\\bin\\jmeter.bat" -n ^
                        -t jmeter-tests\\login.jmx ^
                        -l results\\login.jtl
                        """
                    }
                }

                stage('Search Test') {
                    steps {
                        bat """
                        if not exist results mkdir results
                        "${JMETER_HOME}\\bin\\jmeter.bat" -n ^
                        -t jmeter-tests\\search.jmx ^
                        -l results\\search.jtl
                        """
                    }
                }

                stage('Checkout Test') {
                    steps {
                        bat """
                        if not exist results mkdir results
                        "${JMETER_HOME}\\bin\\jmeter.bat" -n ^
                        -t jmeter-tests\\checkout.jmx ^
                        -l results\\checkout.jtl
                        """
                    }
                }
            }
        }
    }
}
