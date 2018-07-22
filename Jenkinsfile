node('trendyol-hello-world') {
     stage('Cleanup')
    {
        sh("ls -a | xargs sudo rm -rf || /bin/true")
        checkout scm
    }
    stage('Build with Cake')
    {
        sh("sudo chmod +x build.sh")
        sh("./build.sh")
    }
    stage('Build Docker')
    {
        sh("sudo docker build -f HelloWorld/Dockerfile . -t 765584129419.dkr.ecr.us-east-1.amazonaws.com/helloworld")
    }
    stage('Publish Docker')
    {
        sh("eval sudo \$( ~/bin/aws ecr get-login --region eu-west-2 --no-include-email )")
        sh("sudo docker push 765584129419.dkr.ecr.us-east-1.amazonaws.com/helloworld:latest")
    }
}