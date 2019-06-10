Design Doc
===

The basics of how this system will run
1. There will be a main Jenkins node where all jobs will be scheduled
1. There will be 1 or more Jenkins slave where the build jobs will actually be run on
1. There will be at least 4 Jenkins jobs
    1. A job to build and unit test the absolute_api. It will output a docker image as an artifact to a docker registry
    1. A job to create and update our kubernetes cluster (our operations code base will change as we go)
        - this will run by cloning this repo and running ansible playbooks as required
        - there will be a jenkins lock/mutex on the environment to make sure other jobs don't update at the same time
    1. A job to update our new kubernetes cluster with the latest absolute_api docker image 
    1. A job to perform integration testing against this kubernetes environment
1. All of the jenkins jobs will be setup so 

Jenkins notes
- we will be using jenkins groovy scripting plugin to make sure each repo is responsible for configuring their own jenkins job in code.
- we will be using the jenkins pipelines plugin to get a better picture of how each build links to the next one
- the 4 jobs listed will 