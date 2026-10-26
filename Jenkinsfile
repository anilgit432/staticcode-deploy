pipeline {
  agent none
  stages {
    stage ('checkout'){
      agent{
        label 'jenkin-1'}
      steps {
        git branch: 'main',url:'https://github.com/anilgit432/staticcode-deploy.git'
      }
    }
    stage ('deploy'){
      agent{
        label 'jenkin-1'}
      steps {
        sh '''
        echo "===== CONTROLLER NODE ====="
        hostname
        sudo cp index.html /var/www/html/index.html
        sudo systemctl restart apache2 
        '''
      }
        }
    stage ('verify website'){
    agent{
      label 'jenkin-1'}
    steps{
      sh '''

                curl http://localhost
                '''
    }
    }
  }
}
