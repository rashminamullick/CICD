# Merging code with Git branches (Dev and Main)
* Below, I have created a guide to show how to merge code from the Dev branch to our Main branch on Jenkins, provided that all tests pass.
  
## Creating Job2
1.	Create a new job in Jenkins, give it an appropriate name Job2-ci-merge > select freestyle project followed by ok.
 
2.	Add a brief description for the job > enable discard old builds and type in 3. Then select GitHub project and copy your project url into the field.
 ![alt text](image/job2image1.png)

 
## Merge Dev to Main
1.	Follow same steps as above to create new job, give it suitable name ie prismika-merge followed by clicking on freestyle project. Then scroll down to source code management, click on add additional behaviour and select merge before build. This allows jenkins to merge dev branch to main.
 ![alt text](image/job2image3.png)
2.	Scroll down to Build environment and select SSH agent, followed by selecting the your pem key.
  ![alt text](image/job2image6.png)

3.	Finally, on post build actions, we need to select Git publisher from the drop down. Click on push only if build succeeds folowed by merge results. This step allows Jenkins to interact with our Git repository and it ensures that the code will only be pushed to the repository if the build is successful. By clicking on Merge Results it confirms that the merge operation was successful.
![alt text](image/job1image9.png)

Testing
After I have made some changes to my local repo and pushed to the dev branch, it should automatically trigger my first job to notify that I have made some changes.
 ![alt text](image/job2image9.png)
If the test has all passed on my first job, it will start the build on my merge job, which will also merge my code and changes from dev to main. Then it will push it out to the main branch. After this has been successful, it should show a blue circle next to your job as well as a sucessful console output.
 ![alt text](image/job1image8.png)
 

