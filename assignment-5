pipeline {
    agent any 
    stages {
        stage('A') {
            steps{
                catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE') {
                    print "Stage A"
                    sh "exit 1"
                    script { stage_result = true }
                }
            }    
        }

        stage('B'){
            when { 
                expression{ stage_result == true }
            }    
            steps{
                print "EXECUTING: Stage B STAGE_A_RESULT: ${stage_result}"
            }    
        }

        stage('C'){
            when { 
                expression{ stage_result == false }
            }    
            steps{
                print "EXECUTING: Stage C STAGE_A_RESULT: ${stage_result}"
            }    
        }
    }
}
