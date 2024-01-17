# cicd

Application security is a critical aspect of the software development life cycle, and integrating it into the CI/CD pipeline is essential for identifying and addressing security vulnerabilities early in the development process. You can run scans as soon as the new code is deployed by the developer.

So let's dive into integrating application security using GitLab CI/CD.

Create a new repository with sample application.

![image](https://github.com/tauh33dkhan/cicd/assets/43419559/d57f7053-54bd-46e6-8bdb-094c00ec3268)

Add .gitlab-ci.yml file, which is also referred as CI/CD configuration file to define the pipeline, for demo we will run basic commands to explore the environment.
```
stages:
  - checking_environment
  - hello_world

demostage1:
  stage: checking_environment
  script:
    - echo "Sample cicd config"
    - pwd
    - ls

demostage2:
  stage: hello_world
  script:
    - echo "hello world"
```

**`stages:`** Used for defining stages a pipeline can have multiple stages such as `build` `deploy` each stage will be executed in order in which it is defined.

**`demostage1:`** Any random name to identify this job.

**`stage:`** Used for defining the stage.

**`script:`** Used for executing commands.

![image](https://github.com/tauh33dkhan/cicd/assets/43419559/ff4c52a3-dd8e-4561-acad-b242879fc11b)

After you commit the file observe that pipeline is automatically started click on the blue circle button appearing near the commit hash to see the results alternatively you can navigate to `Build -> Piepelines` to see the status.

![image](https://github.com/tauh33dkhan/cicd/assets/43419559/6c40213b-1a67-49d8-9b4f-61afe4ae9fb1)

Click on checking_environment job to see the results

![image](https://github.com/tauh33dkhan/cicd/assets/43419559/7eff01d6-d14f-40d2-8f20-10f5283adaa1)

Here you can see the result of all commands that we defined in checking_environment stage.  
![image](https://github.com/tauh33dkhan/cicd/assets/43419559/847ef9ae-9caf-4be9-8cc8-6b96fc9f002c)

- You can observe that the path where our command are executed is `/builds/tauh33dkhan1/cicd-demo` where `/builds` is the default path and rest is our project path which can also be accessed through `$CI_PROJECT_PATH` cicd environment in case you need it.
- The current path also includes our repository files


 Now that you understand how CI/CD pipeline works let's configure it to run dependency scan on our project.
