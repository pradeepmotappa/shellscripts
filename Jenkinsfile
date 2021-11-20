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
        stage("Git Pull")
        {
            steps
            {
                git branch: 'main', url: 'https://github.com/pradeepmotappa/shellscripts.git'
            }
        }
        stage("File Permission")
        {
            steps
            {
                sh 'chmod 755 ${WORKSPACE}/*.sh'
            }
        }
        stage("Run Shell Script")
        {
            steps
            {
                sh '${WORKSPACE}/bashscript.sh'
            }
        }
    }
}
