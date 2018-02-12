#!groovy

node {
    currentBuild.result = "SUCCESS"

    try {

       stage('Checkout'){

          checkout scm
       }

       stage('Compiling'){

          cmd 'mvn clean install'
       }
	   
      stage('Sonar') {
                    //add stage sonar
                    cmd 'mvn sonar:sonar'
                }
	    
	stage('Checkstyle') {
                    cmd 'mvn checkstyle:checkstyle'
                }

               stage('PMD') {
                    cmd 'mvn pmd:check'
                }
      /* stage('mail'){

         mail body: 'project build successful',
                     from: 'devopstrainingblr@gmail.com',
                     replyTo: 'mithunreddytechnologies@gmail.com',
                     subject: 'project build successful',
                     to: 'mithunreddytechnologies@gmail.com'
       }*/
	    
	    

    }
    catch (err) {

        currentBuild.result = "FAILURE"

           /* mail body: "project build error is here: ${env.BUILD_URL}" ,
            from: 'devopstrainingblr@gmail.com',
            replyTo: 'mithunreddytechnologies@gmail.com',
            subject: 'project build failed',
            to: 'mithunreddytechnologies@gmail.com'
            */
        throw err
    }
}
