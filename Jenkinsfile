pipeline {
  agent { label 'test'}
  parameters {
      string defaultValue: 'Title', description: 'Nombre del archivo', name: 'one_title', trim: true
      string defaultValue: 'Content', description: 'Contenido del archivo', name: 'one_content', trim: true
  }
  stages {
    stage ('Create only file') {
      steps {
        script {
          def exists = fileExists("${one_title}.txt")

          if(exists) {
            echo "yes"
          } else {
            echo "not"
            writeFile file: "${one_title}.txt", text: "${one_content}"
          }

          sh 'ls -l'
        }
      }
    }
    stage ('Create folder and file') {
      steps {
        script {
          def exists = fileExists("${one_title}.txt")

          if(exists) {
            echo "yes"
            dir("${one_title}") {
              writeFile file: "${one_title}.txt", text: "${one_content}"
              sh 'ls -l'
            }
          } else {
            echo "not"
          }

          sh 'ls -l'
        }
      }
    }
  }
}