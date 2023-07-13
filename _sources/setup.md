# Setting up your new workspace

0. Enter your assigned folder on lambda :
	
	`$ cd /data/aneurysm/<yourname>`
	
	Your full terminal should now look something like this :
	
	`<yourname>@lambda04:/data/aneurysm/<yourname>$ `
	
	> Whenever you see a "$", it means you should type the command on a new terminal line.
	
1. Copy the necessary folders for inference and training :

	`$ cp -r /data/aneurysm/hakimi93/TutorialTest .`

2. Enter the folder with `$ cd TutorialTest`
	
3. Activate the virtual environment :

    `$ source 2d-env/bin/activate`
	
	This virtual environment contains all the necessary libraries to run our 2D scripts. Once you are done, 
	you will want to exit the virtual environment with `$ deactivate`.

4. Move on to the next tutorial.	
