pipeline {              
agent any       
stages {
    stage ('callParallelJob') {     
        steps {
               script { 
                       ------- Some code------                          
                       
                       def gitCommitterEmail = sh (
                       script: 'git --no-pager show -s --format=\'%ae\'',
                       returnStdout: true
                       ).trim()
                       echo "git committer: ${gitCommitterEmail}"
                       appConfig.gitCommitterEmail = gitCommitterEmail
                       
                       def gitBranch = "${env.GIT_BRANCH}".trim()
                       appConfig.gitBranch = gitBranch
                     
                       def jenkinsBuildUrl = "${env.BUILD_URL}".trim()
                       appConfig.jenkinsBuildUrl = jenkinsBuildUrl
                       
                      def ciData = [
                                   'git': [
                                   'git_repo': "${git_repo}",
                                   'git_branch': "${env.BRANCH_NAME}",
                                   'git_committer': "${gitCommitterEmail}",
                                   'git_commit': "${GIT_COMMIT}"
                                          ],
                               'jenkins': [
                               'build_url': "${env.BUILD_URL}",
                               'job_name': "${JOB_NAME}",
                               'timestamp': "${BUILD_TIMESTAMP}"
                                          ]
                                      ]
                            writeYaml file: 'ci.yml', data: ciData 
        
                            echo 'calling another job'              
                       build job: '<job2Namehere>, parameters: [
                       string(name: 'Testparam', value: "123"),
                       ], propagate: true, wait: false      
                       echo 'called another job'  

                    }
                }
            }
