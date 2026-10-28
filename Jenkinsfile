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
    stage ('deploy to node1'){
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
    stage ('deploy to node2'){
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
    stage ('verify node1'){
    agent{
      label 'newnode'}
    steps{
      sh '''

                curl http://localhost
                '''
    }
    }
    stage ('verify node2'){
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
