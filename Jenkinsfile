pipeline {
agent any
stages {
stage('Descargar Código') {
steps {
echo 'Clonando el repositorio desde GitHub...'
// Cambia esta URL por la tuya
git branch: 'desarrollo', url:

'https://github.com/TU_USUARIO/proyecto-devsecops.git'

}
}
stage('Construir Imagen Docker (Build)') {
steps {
echo 'Construyendo el contenedor seguro...'
sh 'docker build -t mi-app-segura:latest .'
}
}
}
}