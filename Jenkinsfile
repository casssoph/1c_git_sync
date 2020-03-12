def storage_path 
def repository_path 
def loc_storage_copy
def storage_user
def storage_pass

pipeline {
     parameters {
        string(defaultValue: "${env.storage_path}", description: 'Путь к хранилищу 1с', name: 'storage_path')
        string(defaultValue: "${env.repository_path}", description: 'Путь к репозиторию', name: 'repository_path')
        string(defaultValue: "${env.loc_storage_copy}", description: 'Путь к копии хранилища 1с', name: 'loc_storage_copy')
        string(defaultValue: "${env.storage_user}", description: 'Пользователь хранилища', name: 'storage_user')
        string(defaultValue: "${env.storage_pass}", description: 'Пароль пользователя хранилища', name: 'storage_pass')
   }


    agent any
    stages {
        stage('Копирование Хранилища') {
            steps {
                returnCode = utils.cmd('xcopy ${storage_path} ${loc_storage_copy} /Y /E')
         //             if (returnCode != 0) {
          //                 utils.raiseError("Возникла ошибка копирования репозитория")
      //                 }
            }
        }
        stage("Выгрузка в локальный GIT") {
            steps {
                      returnCode = utils.cmd('cd ${repository_path} \n  gitsync sync --storage-user ${storage_user} --storage-pwd=${storage_pass}  ${loc_storage_copy}')
         //             if (returnCode != 0) {
           //                utils.raiseError("Возникла ошибка Выгрузки в локальный гит")
                   //    }
            }
        }
    
    }
}
