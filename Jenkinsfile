node{
  stage('SCM Checkout'){
    git 'https://github.com/praveen-1989/welcometoskillrary-master1.git'
  }
  stage('Compile-Package'){
    bat 'mvn package'
  }
  stage('Email Notification'){
    mail bcc: '', body: '''Hi welcome to jenkins job
    thanks
    praveen''', cc: 'gbpraveen55@gmail.com', from: '', replyTo: '', subject: 'jenkins job', to: 'pravi.pravin5@gmail.com'
  }
}
