node { 
    stage ('prep') {
        checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'e22c3202-01a5-4171-9ea2-b616b5c6a66b', url: 'git@github.com:hardah/gildedrose.git']]])
        echo "cloned git"
    }

    stage ('build') {
        echo "building"
        sh 'docker run -i --rm --name my-maven-project -v "$PWD":/usr/src/mymaven -w /usr/src/mymaven maven:3-jdk-8 mvn install'
        echo "built"
    }

    stage ('results') {
        
    }
}
