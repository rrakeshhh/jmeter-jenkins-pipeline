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

                stage('FirstName Test') {
                    steps {
                        bat """
                        if not exist results mkdir results
                        "${JMETER_HOME}\\bin\\jmeter.bat" -n ^
                        -t jmeter-tests\\HRM_FNAME.jmx ^
                        -l results\\FNAME.jtl
                        """
                    }
                }

                stage('MiddleName Test') {
                    steps {
                        bat """
                        if not exist results mkdir results
                        "${JMETER_HOME}\\bin\\jmeter.bat" -n ^
                        -t jmeter-tests\\HRM_MNAME.jmx ^
                        -l results\\MNAME.jtl
                        """
                    }
                }

                stage('LastName Test') {
                    steps {
                        bat """
                        if not exist results mkdir results
                        "${JMETER_HOME}\\bin\\jmeter.bat" -n ^
                        -t jmeter-tests\\HRM_LNAME.jmx ^
                        -l results\\LNAME.jtl
                        """
                    }
                }
            }
        }
    }
}
