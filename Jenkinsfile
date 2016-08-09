node {
   // Mark the code checkout 'stage'....
   stage 'Checkout'

   // Checkout code from repository
   checkout scm

   // Run the server
   stage 'Start Server'
   sh ". /etc/simple_travel.env && ./manage.py runserver localhost:8000&"

   stage 'Load Test'
   sh "cd load_tests && ./post-commit.yml"

   stage 'Kill Server'
   sh "kill `ps ax | grep '[/]usr/bin/python ./manage.py runserver' | awk '{print \$1}'`"
}
