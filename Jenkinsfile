pipeline {
    agent any
    stages{
        stage('clone the repo and removing the existing one')
        {
          steps {
              sh "sudo rm -rf /home/localadmin/project"
              sh "cd /home/localadmin/"
              sh "mkdir -p /home/localadmin/project"
              sh "cd /home/localadmin/project"
              sh "git clone https://github.com/aamirsaleemkudcs/apacheweb.git /home/localadmin/project"
               
               }
         }
         
		  stage("Installing the webserver and starting its service")
          {
            steps
            {
              sh "sudo apt install apache2 -y"
              sh "sudo systemctl start apache2"
            }
          }
         		 
         stage("copying files to /var/www/html")
         {
           steps 
           {
              sh "sudo cp /home/localadmin/project/www/html/index.html /var/www/html/"
           }
          }
                         
          stage("Restarting the apache2 service")
          {
            steps
            {
              sh "sudo systemctl restart apache2"
            }
          }
               
    }

}
