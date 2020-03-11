
pipeline {
    agent any
    stages {
        stage('Копирование Хранилища') {
            steps {
                returnCode = utils.cmd("xcopy \\nng9-v-1c-03\partkom83_2019 C:\partkom83_2019 /Y /E")
                      if (returnCode != 0) {
                           utils.raiseError("Возникла ошибка копирования репозитория")
                       }
            }
        }
        stage("Выгрузка в локальный GIT") {
            steps {
                      returnCode = utils.cmd("cd C:\1CTeamDevops\GitRepositories\Partkom83_2019
                      gitsync sync --storage-user kalinin --storage-pwd=123 C:\partkom83_2019")
                      if (returnCode != 0) {
                           utils.raiseError("Возникла ошибка Выгрузки в локальный гит")
                       }
            }
        }
    
    }
}
