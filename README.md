# FITS CTF Submissions

## Creating a new challenge


- Create an issue called "[difficulty][topic][yourname]#" where:
    - Difficulty is beginner, intermediate, advanced. Use your best judgement but don't worry about it too much. 
    - Topic is (probably) linux, web, or windows. If it really doesn't fit into these categories use your best judgment.
    - \# is for if you've submitted more than one challenge you can increment this to make the name unique.
    - You will be assigned a port number for your dockerfile and configurations.
- Fork the project by clicking the "fork" button in the top right
- Clone the forked project and add the following:
    - Add a directory called roles/[difficulty][topic][yourname] - this is where all the challenge files go
    - Inside of challenge# add:
        - A folder called `docker`
        - A folder called `tasks`
        - A file called <span>`readme.md`</span> which will have the details of the challenge
        - A file in `tasks` called `main.yml`
        - A file in docker called `Dockerfile`
        - a folder called `resouces` if you need things like config files and webpages copied to the challenge vm/container
- When you're done you will create a pull request which is essentially you asking to take your code and merge it with the master copy. It will be reviewed and if approved it will be deployed automatically to the public test server.

### Dockerfiles

If your challenge is using docker, you will need a Dockerfile. It should contain most of what you need in the container for the challenge. Use beginnerlinux1's dockerfile as an example. 

The dockerfile will handle setup such as:

- What operating system you want the container to run
- What packages you need installed
- Removing unncessary packages
- Creating files, echoing into files (like flags), permissions of files
- Copying files from the host machine to the container (config files, webpages, databases, etc)

As things come up I will make this overview more thorough.

### Creating tasks in tasks/main.yml

The main ansible tasks.yml file has 2 roles:

#### When used with docker:
- Get the dockerfile and necessary resources from orchestrator to the CTF-Challenges VM
- Kickoff docker build to build the image
- Start the container

### Port Number

Your challenge needs to be listening on a port in order for people to access it, but if two people submit a challenge at the same time with the same port numbers it will break the build to the public test server. To prevent this, please make an issue with your difficult and topic in the title, and a port number will be assigned. Eventually ctfbot will be able to spit out port numbers automatically.

### Testing your challenge

Once your challenge has been merged to the master branch, it will automatically be deployed to the public test server where you'll find it at 192.168.10.13:[PORT], where [PORT] is the port you were assigned.

## Examples

I've added 2 examples, [one web challenge](roles/beginnerwebelliot1/readme.md) and [one linux challenge](roles/beginnerlinuxelliot1/readme.md)

If you need help creating a challenge, make an issue and describe what your idea is. Also go ahead and fork the code and give it a whirl and then we can suggest edits easier.
