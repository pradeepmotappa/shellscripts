pipeline
{
    agent any
    options
    {
        buildDiscarder logRotator(daysToKeepStr:'2', numToKeepStr:'2', artifactDaysToKeepStr:'2', artifactNumToKeepStr:'2')
        timestamps()
    }
    triggers
    {
        pollSCM '* * * * *'
    }
    stages
    {
        stage('Git Poll')
        {
            steps
            {
                git branch: 'main', url: 'https://github.com/pradeepmotappa/shellscripts.git'
            }
        }
        stage('Change Permission')
        {
            steps
            {
                chmod "755 ${WORKSPACE}/bashscript.sh"
            }
        }
        stage('Script Run')
        {
            steps
            {
                sh "${WORKSPACE}/bashscript.sh"
            }
        }
    }
}
