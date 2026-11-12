pipeline{
    agent {
        label 'Agent-SPC'
    }
    parameters{
        choice(
            name:'Git_Branch',
            choices:['develop','main','master'],  
            description:'Git_Branch_Switching'
            //first value is the default value
        )
    }
    stages{
        stage('Git_Checkout'){
            steps{
               git branch: params.Git_Branch, 
               url: 'https://github.com/PRDevopsProjects/Jenkinsfile_ChoiceParameter_SPC.git'
            }

        }
        stage('SPC_BUILD_and_RUN_App'){
            steps{
                sh 'mvn clean package'
                sh 'java -jar target/spring-petclinic*.jar'
            }
        }
        stage('Project_info'){
            steps{
                echo "Branch_Name: ${params.Git_Branch}"
                sh 'pwd'
                sh 'mvn --version'
                sh 'whoami'
                }
        }
    }
}