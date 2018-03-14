pipeline {
   agent any

   stages {
      stage('Gem Installation') {
         steps {
            echo 'Updating Gemfiles...'
            sh 'BUNDLE_GEMFILE=Gemfile bundle install --deployment --clean'
         }
      }
      stage('Build and Deploy Jekyll') {
         steps {
            echo 'Building and deploying'
            sh 'bundle exec jekyll build -d /www/ajfite.com/projects/tractorhacking/'
         }
      }
   }
}
