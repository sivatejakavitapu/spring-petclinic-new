pipeline{
    agent { label 'NODE_2'}
        parameters 
        {
           choice (name: 'testpara', choices: ['main'], description: '') 
        }
        stages
        {
            stage ('download')
            {
                steps
                 {
                    git branch: 'main', url: 'https://github.com/sivatejakavitapu/spring-petclinic-new.git'
                }

            }
        }
}