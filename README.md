# covid-19-project(MACHINE LEARNING INTEGIRATION WITH DEVOPS)
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
