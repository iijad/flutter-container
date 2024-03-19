## DevContainer Environment
### What is a DevContainer?
- A DevContainer is a precontained environment for software development, typically using containerization technology such as Docker. 
- Its main role is to provide developers with a consistent and reproducible environment for coding, testing, and debugging their applications like with Flutter apps. 

### Configuration of Dev Container 
1. First, download [Docker Desktop](https://www.docker.com/products/docker-desktop/) in order to be able to make containers. Make sure you also have [Visual Studio Code](https://code.visualstudio.com/download) installed as well. Get the adjacent ***Dev Containers***  and ***Docker*** extensions on VS Code so you can open any folder in a container. 
2. Click the arrows on the bottom left corner of Visual Studio Code. Select ***Add Dev Container Configuration Files***. Then click ***Add configuration to workspace***. For this container, the __Ubuntu__ template was used, so we have the Ubuntu jammy image. 
3. Within the ***.devcontainer***, there is the ***devcontainer.json*** file where the container was configured. In the file, the image of the container was moved to a ***Dockerfile*** along with the instructions to build the flutter container. The .json file has ***postCreateCommands*** for when after the container is built, and in this case the commands are to create a directory for  ***/opt/flutter*** so the user can have write permissions, along with exporting ***CMAKE*** for the container in order to build on linux. 
4. The other part of the .json file is the customizations, where I installed the necessary Linux packages in order to run the flutter apps in linux. 
5. For the ***Dockerfile***, I detailed the steps needed to download and use Flutter for this container environment, which include obtaining the ***CMAKE*** tools, installing the Flutter and Dart SDK, and obtaining ownership of the files in order to use them in the container. 

### Starting and using the DevContainer 
1. After setting up the container, click the blue arrows at the bottom left hand corner of Visual Studio Code. 
2. Click the ***Reopen In Container*** option.
3. Wait as the Dev Container builds. 
4. After it builds, you can now create Flutter apps in the container. Go to the ***command line*** by either clicking the error and warning buttons at the bottom left next to ***main***, or use ```Ctrl + Shift + P``` and type ***Shell Command*** to access it. type ```flutter create (name of app)``` on the command line, and then type ```cd (name of app)``` to access the folder. 
5. Edit or create the Flutter app by accessing the ***lib*** section of the Flutter app and editing the ***main.dart*** file. By default, the default app is already created in Flutter. 
6. When you finish editing the app, push changes to folder/directory, and then click the blue arrows and choose the ***Rebuild Container*** option. 
7. To run the app, go back to the command line and type ```flutter run``` to run the app. It will run the app on the default web app on your computer. 

### Challenges of Container Building
- Some of the challenges of building the container included trying to set up ownership of the /opt/flutter directory. I ended up having to make the directory as a ***postCreateCommand*** as well as using sudo in front of the command to make sure it worked, even though I sacrificed some security in the process.
- Another challenge was with the .json file, and with the ***settings*** part of the customization. I thought you can have the settings outside of the customization, but there were errors everytime. I ended up putting the settings under the customizations in order for it to work. 
- I had trouble with pushing my saved work to the directory, as it was marked unsafe by VSCode. I ended up having to mark the directory as safe, and I had to configure the username on the command line. 

### Conclusion
**There are many benefits of using a DevContainer:**
- It ensures that if multiple people are using it, they are all working under the same consistent environment, ensuring consistent results across different machines.
- It can be easily reproducible across different platforms and machines, ensuring consistent results.
- It is a scalable solution for managing the complexiity of Flutter projects as they grow, as they encapsulate the development environment within a containerized environment, making it easier to manage dependencies and configurations.

**I gained some insights throughout this process:**
- I learned about how multiple people on a team can use a DevContainer for any project that they could have, as it can reduce time on setting up environments.
- Because one spends less time on creating the enviroment, more focus can be put on the project and the source code as the rest of the process is set up. 
- The Containers streamline the process of maintaining and updating the development environment, as changes can be made to the container configuration without affecting the host system, ensuring a clean and stable development environment over time.
