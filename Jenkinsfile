pipeline {
  agent none
  stages {
    stage ('checkout'){
      agent{
        label 'newnode'}
      steps {
        git branch: 'main',url:'https://github.com/anilgit432/staticcode-deploy.git'
      }
    }
    stage ('deploy'){
      agent{
        label 'newnode'}
      steps {
        sh '''
        hostname
        sudo cp index.html /var/www/html/index.html
        sudo systemctl restart apache2 
        '''
      }
        }
    stage ('deploy'){
      agent{
        label '2nd new node'}
      steps {
        git branch: 'main',url:'https://github.com/anilgit432/staticcode-deploy.git'
        sh '''
        hostname
        sudo cp index.html /var/www/html/index.html
        sudo systemctl restart apache2 
        '''
      }
    }
    stage ('verify website'){
    agent{
      label 'newnode'}
    steps{
      sh '''

                curl http://localhost
                '''
    }
    }
    stage ('verify website'){
    agent{
      label '2nd new node'}
    steps{
      sh '''

                curl http://localhost
                '''
    }
    }
  }
}
