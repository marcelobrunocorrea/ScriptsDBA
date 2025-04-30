pipeline {
    agent any

    environment {
        FLYWAY_HOME = 'C:\\Program Files\\Red Gate\\Flyway Desktop'
        FLYWAY_CONF = 'flyway.conf'
    }

    stages {
        stage('Clonar Repositório') {
            steps {
                git branch: 'main', url: 'https://github.com/Lucasjesus1308/ScriptsDBA.git'
            }
        }

        stage('Verificar Flyway') {
            steps {
                bat "\"${FLYWAY_HOME}\\flyway\" -v"
            }
        }

        stage('Executar Flyway Info') {
            steps {
                bat "\"${FLYWAY_HOME}\\flyway\" -configFiles=${WORKSPACE}\\${FLYWAY_CONF} info"
            }
        }

        stage('Executar Migração') {
            steps {
                bat "\"${FLYWAY_HOME}\\flyway\" -configFiles=${WORKSPACE}\\${FLYWAY_CONF} migrate"
            }
        }
    }
}
