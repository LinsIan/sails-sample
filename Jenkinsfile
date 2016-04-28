node {

   stage 'checkout project'
   git url: 'https://github.com/TrunkWorkshop/sailsSample.git'

   stage 'docker env check'

   sh "docker -v"
   sh "docker-compose -v"
   sh "docker ps"

   stage 'build docker node env'
   sh "docker build -t agileworks/sails_sample_env dockers/node"

   stage 'build project'
   sh "docker-compose run --rm buildDev"

   stage 'test project'
   sh "docker-compose run --rm test"

   stage 'build production image'
   sh "docker build -t agileworks/sails_sample_prod ."

   stage 'publish production image'
   sh "docker push agileworks/sails_sample_prod"

}
