pipeline {
agent any
parameters {
string(name: 'PERSON' , defaultValue: 'Chrissy', description: 'say hello')
choice(name: 'CHOICE' , choices: ['1','2','3','4'], description: 'pick')
password(name: 'PASSWORD' , defaultValue: '1234', description: 'enter pass')
}
stages {
stage('name') {
steps {
echo "Hello ${params.PERSON}"
}
}
stage('choice') {
steps {
echo "Choice ${params.CHOICE}"
}
}
stage('password') {
steps {
echo "Password: ${params.PASSWORD}"
}
}
}
