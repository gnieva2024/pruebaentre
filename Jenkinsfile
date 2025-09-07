pipeline {
    agent any

    stages {

        stage('Clean Report Folder') {
            steps {
                // Borra la carpeta report si existe
                bat 'rmdir /s /q C:\\Users\\Graciela\\jmeter\\report'
            }
        }

        stage('Checkout') {
            steps {
                // Clona tu repositorio
                git branch: 'main', url: 'https://github.com/gnieva2024/pruebaentre.git'
            }
        }

        stage('Run JMeter Test') {
            steps {
                // Ejecuta tu test JMeter en modo no-GUI
                bat '"C:\\Users\\Graciela\\Downloads\\Apache jmeter\\apache-jmeter-5.6.3\\bin\\jmeter.bat" -n -t C:\\Users\\Graciela\\jmeter\\pruebaentre.jmx -l C:\\Users\\Graciela\\jmeter\\results.jtl -e -o C:\\Users\\Graciela\\jmeter\\report'
            }
        }

        stage('Archive Report') {
            steps {
                // Guarda la carpeta report como artifact
                archiveArtifacts artifacts: 'C:\\Users\\Graciela\\jmeter\\report\\**', fingerprint: true
            }
        }
    }
}
