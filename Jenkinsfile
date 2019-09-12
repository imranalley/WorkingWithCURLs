import groovy.json.JsonSlurper

pipeline {
    agent any
    stages {
        stage ('Call API'){
            steps{
                withCredentials([usernamePassword(credentialsId: 'GitHubID', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]){
                    script{
                        config.OUTPUT = sh "curl -i -H \"Authorization: token $PASSWORD\" https://api.github.com/users/imran-kkz" 
                    }
                }
            }
        }
        stage ('Parse API Call'){
            steps{
                def jsonParse = null
                jsonParse = new JsonSlurper().parseText(config.OUTPUT)
                def output = jsonParse.body
                echo output
            }
        }
    }
}
