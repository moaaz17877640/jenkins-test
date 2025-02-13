node{

    git branch: 'master'  url: 'https://github.com/moaaz17877640/jenkins-test.git'
   stage('Build'){
       sh 'echo "Building the app"'
       try{
           sh 'echo "Testing the app"'
       }catch(Exception e){
           currentBuild.result = 'FAILURE'
           throw e
       }
   }
    
   
  stage('test'){
    if(env.BRANCH_NAME == 'master'){
        sh 'echo "Testing the app"'
    }else{
        sh 'echo "non Testing the app"'
    }
       sh 'echo "Building the app"'
   }
    

}