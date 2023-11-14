## Building and running the container
With all our config files setup, let's build and run the container! After the loads of terms we encountered, building and running the container is way simpler. It will only involve few commands.

### 1. In your terminal, run `docker-compose build`
Running this command will get Dockerfile and install all the necessary things to make a rails development environment. Note that the installation may take a while because docker will need to download the necessary packages.

### 2. In your terminal, run `docker-compose run --rm --service-ports ruby_dev`
This command will start a bash terminal that will be your rails development environment where the rails commands are available. With only these two commands, and two config files, you already have a rails environment without even going through a log of troubleshooting! Notice that our command has some flags, `--rm` means remove the container after using it, and `--service-ports` means use port 3000 in our container so we can see our rails server in action. The name `ruby_dev` also came from services found at our `docker-compose.yml`.

## Test-run a rails app
Now that we've successfully made our rails development environment, we'll test a sample rails app.

### 1. Run `rails new myapp && cd myapp`
This command will create a new rails app in a folder named myapp. After that the terminal will go the folder. You can name it whatever you want.

### 2. Update and install gems. Run `bundle update && bundle install`
Just make sure you're in the right folder, in `myapp`, which contains the rails app files. This command will update and install your dependencies.

### 3. Test the server by running `rails server -p $PORT -b 0.0.0.0`
Remember the port we specified in our Dockerfile before? This is where we can use it. In our case, rails will use port 3000 to start the server. Don't forget to put `-b 0.0.0.0` because you won't see the app on your local machine without this.

### 4. Stop the server by pressing `ctrl-d` on your keyboard.
#### Cleaning Up
After you're done with everything, you can `exit` on your container by running exit on your container's bash terminal. The `--rm` flag you typed before will remove the container, but will you get to keep your ruby on rails files.

### Run `docker-compose down` to cleanup
Cleaning up is when you're done with the project, and you want to remove your dev environment so you can save space. If you're really done, you can use this command. Docker will remove all your setup, and the images you downloaded. This so powerful, because, imagine you followed a lot of steps and a lot of installation on your mac. The only way to remove that setup is to uninstall them one by one. With docker on our side, it's just one command. Aww yeah!