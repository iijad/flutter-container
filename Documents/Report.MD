### What is a DevContainer?
- A DevContainer is a precontained environment for software development, typically using containerization technology such as Docker. 
- Its main role is to provide developers with a consistent and reproducible environment for coding, testing, and debugging their applications like with Flutter apps. 
- Allivates worry for configuring an environemnt for devs, allows them to focus on the applciation building

###  Configuration of Dev Container 
1. First, download [Docker Desktop](https://www.docker.com/products/docker-desktop/) in order to be able to make containers. Make sure you also have [Visual Studio Code](https://code.visualstudio.com/download) installed as well. Get the adjacent ***Dev Containers***  and ***Docker*** extensions on VS Code so you can open any folder in a container. 
2. Click the arrows on the bottom left corner of Visual Studio Code. Select ***Add Dev Container Configuration Files***. Then click ***Add configuration to workspace***. For this container, the __Ubuntu__ template was used, so we have the Ubuntu jammy image. 
3. Within the ***.devcontainer***, there is the ***devcontainer.json*** file where the container was configured. In the file, the image of the container was moved to a ***Dockerfile*** along with the instructions to build the flutter container. The .json file has ***postCreateCommands*** for when after the container is built, and in this case the commands are to create a directory for  ***/opt/flutter*** so the user can have write permissions, along with exporting ***CMAKE*** for the container in order to build on linux. 
4. The other part of the .json file is the customizations, where I installed the necessary Linux packages in order to run the flutter apps in linux. 
5. For the ***Dockerfile***, I detailed the steps needed to download and use Flutter for this container environment, which include obtaining the ***CMAKE*** tools, installing the Flutter and Dart SDK, and obtaining ownership of the files in order to use them in the container. 


### CI/CD Pipeline Environment

- The CI/CD Pipeline operates within the Github ecosystem, leverging GitHub Actions. Github Actions provides a flexible integrated environment for automating the software development lifecycle. The infrastructure primarily consists of the cloud-based services, enabling seamless integration with our version control system. Our target operating system for the pipeline is Linux, ensuring compatibility across various deployment environments. Additionally, network configurations are optimized to facilitate secure and efficient communication between the CI/CD pipeline components and external systems. 

### CI/CD Pipeline Tools

- **GitHub Actions**: GitHub Actions was chosen as the primary tool for our CI/CD pipeline due to its tight integration with GitHub repositories, ease of setup, and extensive library of actions. Its features include support for various programming languages, containerization, and customizable workflows. GitHub Actions excels in automating workflows triggered by events such as pushes, pull requests, or scheduled tasks. While GitHub Actions offers robust capabilities, it may have limitations in complex build scenarios or large-scale enterprise deployments.

 ### Automation Process

 1. **Code Compilatioon** -  Upon a push or pull request event, the CI/CD pipeline triggers a workflow to compile the codebase. This step involves fetching the latest code changes and running the appropriate build commands specified in the project configuration.
 2. **Unit Testing** - Following successful compilation, the pipeline executes unit tests to ensure code integrity and identify any regressions. Unit tests are essential for validating the functionality of individual components in isolation.
3. **Integration Testing** - Upon passing unit tests, the pipeline proceeds to integration testing, where the application is deployed to a staging environment resembling the production setup. Integration tests simulate real-world interactions between different modules or services to validate end-to-end functionality and compatibility.
4. **Deployment** -  If all tests pass, the pipeline automatically deploys the application to the production environment. Deployment involves packaging the application artifacts, provisioning resources, and orchestrating the deployment process using infrastructure-as-code tools such as Terraform or Kubernetes manifests.

### Flutter Application
- The application is the default flutter app, an app to detail how many times a user clicks the button.
- The simplicity of the app allowed for testing the pipeline on a small scale.
- Demonstrated the tests (smoke test) that would be run for the flutter application. 

 ### Challenges of Container Building
- Some of the challenges of building the container included trying to set up ownership of the /opt/flutter directory. I ended up having to make the directory as a ***postCreateCommand*** as well as using sudo in front of the command to make sure it worked, even though I sacrificed some security in the process.
- Another challenge was with the .json file, and with the ***settings*** part of the customization. I thought you can have the settings outside of the customization, but there were errors everytime. I ended up putting the settings under the customizations in order for it to work. 
- Flutter Versions: Needed to download the beta version of flutter instead of the stable version to resolve depdancies within the build phase. Also needed to delete original app to replace it with the right flutter version.

### Conclusion
- Learned about the process of building a dev container. 
- Gained skills in building a CI/CD container 
- Learned about building a scalable team solution to working on different parts of the same project. 
