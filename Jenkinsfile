node { 
    stage ('prep') {
        git 'https://github.com/hardah/gildedrose'
        echo "cloned git"
    }

    stage ('build') {
        echo "building"
        sh 'docker run -i --rm --name my-maven-project -v "$PWD":/usr/src/mymaven -w /usr/src/mymaven maven:3-jdk-8 mvn install'
        echo "built"
    }

    stage ('results') {
        junit '**/target/surefire-reports/TEST-*.xml'
        archive 'target/*.jar'
        echo 'test'
    }
    
    stage ('doc') {
        sh 'docker run -i --rm --name my-maven-project -v "$PWD":/usr/src/mymaven -w /usr/src/mymaven maven:3-jdk-8 mvn site'
        archive 'target/site/**/*'

}
