# covid-19-project(MACHINE LEARNING INTEGRATION WITH DEVOPS)
Many of the people simply just learn Machine learning and build their Projects but the automation part which is also needed is never implemented . The implementation of Machine learning with DevOps is what the Industry needs. 
And this is the reason why most of the projects in Machine learning fails.
# I would like to thank Mr. Vimal Daga for giving us such a great opportunity to learn and grow under him and create such a industry needed project

# WHAT MY PROJECT IS ABOUT ?
I have trained my machine learning model (which basically predicts the corona virus in the chest x ray of a person and tells whether the person is infected or not) and automated the task with the devops to get the best accuracy available for the model.

# TASK:
1. Create container image that’s has Python3 and Keras or numpy installed using dockerfile
2. When we launch this image, it should automatically starts train the model in the container.
3. Create a job chain of job1, job2, job3, job4 and job5 using build pipeline plugin in Jenkins
4. Job1 : Pull the Github repo automatically when some developers push repo to Github.
5. Job2 : By looking at the code or program file, Jenkins should automatically start the respective machine learning software installed interpreter install image container to deploy code and start training( eg. If code uses CNN, then Jenkins should start the container that has already installed all the softwares required for the cnn processing).
6. Job3 : Train your model and predict accuracy or metrics.
7. Job4 : if metrics accuracy is less than 80% , then tweak the machine learning model architecture.
8. Job5: Retrain the model or notify that the best model is being created

# WORK DONE :
1. firstly let me show you the docker file i used in order to create my docker container up and running with tensorflow , keras and other modules in it.
![Screenshot (396)](https://user-images.githubusercontent.com/51692515/82863028-b879cc00-9f3e-11ea-9bde-ae76e3d3ab3d.png)

2. Next i created the code for training my model , sending the mail , and a config.yaml file which is basically used for tweaking our model . the code for the same is present in the above github repo.

3. I created the remote hooks so , that the code is automatically pushed on to git hub and then downloaded in the github workspace i created using jenkins so that it can be deployed in container.
![Screenshot (399)](https://user-images.githubusercontent.com/51692515/82863415-bb28f100-9f3f-11ea-9eb0-d1c001147d38.png)

4. Now let my show you the task/jobs created in the jenkins to automate the process.
![Screenshot (392)](https://user-images.githubusercontent.com/51692515/82863633-40140a80-9f40-11ea-8a70-63ab50a4d937.png)

So , i created these four jobs using the build pipeline in jenkins:
1. github( it will pull all the code from the git hub)
2. create container(which would mount the workspace where the code is present and run the container)
3. accuracy (which would predict the accuracy and mail it to the user in order to get the progress report)
4. tweaking model(which would tweak our model and train it again in order to get the better accuracy)

NOW LET'S HAVE A LOOK AT EACH STEP IN DETAIL:

# GIT HUB:
we triggered git hub using the trigger build remotely option . The jenkins configuration is as shown below :

![Screenshot (401)](https://user-images.githubusercontent.com/51692515/82864218-b36a4c00-9f41-11ea-839c-8142546ea4b0.png)

![Screenshot (402)](https://user-images.githubusercontent.com/51692515/82864223-b5340f80-9f41-11ea-9377-6ab4714d032f.png)

we are using the remote workspace to mount on to our docker container thats why we didnt change the mounting directory. but one can change as per the requirement.
we created create container as a downstream project for git hub.

# CREATE CONTAINER:
create container has a upstream project git hub , which will trigger it when it is succesfully executed.
Now, let me show the configuration of the create container job.


![Screenshot (405)](https://user-images.githubusercontent.com/51692515/82864643-9f731a00-9f42-11ea-86af-2933c6bfe00e.png)

![Screenshot (406)](https://user-images.githubusercontent.com/51692515/82864646-a13cdd80-9f42-11ea-879d-a05a5a1f5cc3.png)

The above configuration will create a container and start the model training in the container.
The downstream project is the accuracy job . so , it will be triggered once the create container job is finished.

# ACCURACY:
Now, let me show the accuracy job configuratuion:
![Screenshot (407)](https://user-images.githubusercontent.com/51692515/82864959-566f9580-9f43-11ea-8c14-86aaac5b0c28.png)

![Screenshot (408)](https://user-images.githubusercontent.com/51692515/82864963-58d1ef80-9f43-11ea-96fb-8b00e2a19961.png)

firstly , it would mail the accuracy of the project to the user . The code for mail.py is present in the repo above.
Next, it will check the accuracy . if it is less than 80 % then the model will be tweaked else the model will not be tweaked and the job will fail with exit 1.

# TWEAKING MODEL:
It is a downstream project of the accuracy job . once it is triggered it will start tweaking the model and then train the model again with the tweaked code.
the tweaked code is as shown below:
![Screenshot (409)](https://user-images.githubusercontent.com/51692515/82865343-207ee100-9f44-11ea-8fb4-c0d7f9013f07.png)

The downstream project for tweaking model is create container . once it is completed it again looks for the container.

# WORKING IN ACTION:
The best part is to visualize through the images or video.
So , here are the images in order to get what is happening in the project.
 
![Screenshot (392)](https://user-images.githubusercontent.com/51692515/82869080-4f4c8580-9f4b-11ea-83b6-8ab918c54134.png)

![Screenshot (393)](https://user-images.githubusercontent.com/51692515/82869090-52e00c80-9f4b-11ea-86fb-2075050c8ba3.png)

![Screenshot (394)](https://user-images.githubusercontent.com/51692515/82869097-54113980-9f4b-11ea-814b-ad065768da1d.png)

![Screenshot (395)](https://user-images.githubusercontent.com/51692515/82869100-55426680-9f4b-11ea-8050-6a03af5dd77c.png)

![Screenshot (397)](https://user-images.githubusercontent.com/51692515/82869111-58d5ed80-9f4b-11ea-88d5-ab1d5584e04f.png)

![Screenshot (398)](https://user-images.githubusercontent.com/51692515/82869121-5bd0de00-9f4b-11ea-867d-a76ed6077643.png)

![Screenshot (400)](https://user-images.githubusercontent.com/51692515/82869134-60959200-9f4b-11ea-8e0c-658126ff9909.png)

![Screenshot (403)](https://user-images.githubusercontent.com/51692515/82869143-63908280-9f4b-11ea-944e-63bd3c5bbcf8.png)

![Screenshot (404)](https://user-images.githubusercontent.com/51692515/82869154-68553680-9f4b-11ea-9752-9ac215160b9c.png)










# REFERENCES:
The above project i created was very awesome and great for me .
1.https://www.youtube.com/
2.https://stackoverflow.com/
3.https://www.geeksforgeeks.org/


