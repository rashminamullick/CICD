# What is Jenkins?
* Jenkins is an open-source automation tool that helps test and build applications automatically.
Instead of running tests manually, Jenkins does this work for us every time code changes, which makes the process faster, more reliable, and less error-prone.

## In this project, Jenkins is used to:
* Pull code from GitHub
* Run tests automatically
* Stop the pipeline if something is broken

### Why Job 1 Exists in the Pipeline

Only allow tested, working code to move forward.
* Broken code never reaches production
* Problems are found early
* Developers get fast feedback

## Creating Job 1 in Jenkins (Step by Step)

## Step 1: Create a New Jenkins Job

### After logging into Jenkins:
* Click New Item
* Enter the job name:
* rashmina-sparta-app-job1-ci-test
* Select Freestyle project
* Click OK

### Why I chose Freestyle
* It gives full control and is ideal for learning and demonstrating CI clearly.


## Step 2: Adding a Clear Job Description

![alt text](Job1-image/job1-job_description.png)

### In the General section, I added a short description:

* “Runs automated CI tests and triggers builds using a webhook.”

![alt text](Job1-image/job1-configure.png)

###  Why this matters:
* Anyone viewing the job can immediately understand its purpose.

## Step 3: Manage Build History (Stability & Performance)
### I enabled Discard old builds and set:
* Maximum builds to keep: 5
  ![alt text](Job1-image/job1-max_build.png)
  
   

### Why this matters:
* This prevents Jenkins from using unnecessary disk space and keeps the system stable over time.

### Source Code Management (Connecting GitHub)
## Step 4: Configure GitHub Repository

### In Source Code Management:
![alt text](Job1-image/job1-source_code_management.png)

* Selected Git
* Added the repository URL:
    git@github.com:rashminamullick/tech515-sparta-test-app-cicd.git

![alt text](Job1-image/job1-test_repository.png)
* Selected stored SSH credentials

  ### Why SSH is used:
* SSH is more secure than passwords and allows Jenkins to access GitHub safely.

## Step 4a: Configure Jenkins SCM Credentials (SSH)

To allow Jenkins to securely access the GitHub repository, SSH credentials were configured in Jenkins and linked in the SCM section.

### Steps taken:
1. Generated an SSH key pair locally.
2. Added the **public key** to GitHub under:
   Settings → SSH and GPG keys.
3. Added the **private key** to Jenkins:
   - Jenkins → Manage Jenkins → Credentials
   - Added **SSH Username with private key**
   - Username: git
4. Selected this SSH credential in the **Source Code Management** section of Job 1.


![alt text](Job1-image/job1-source_code_management.png)

### Why this is important:
* Jenkins can access GitHub securely without passwords
* Credentials are stored safely in Jenkins
* This setup supports automation and CI/CD best practices

## Step 5: Specify the Branch to Build
### Why dev branch?
* All testing happens on the development branch before anything reaches main.
### In Branches to build, I set:
    */dev

![alt text](Job1-image/job1-branches_to_build.png)
  ## Step 5a: Configure GitHub Webhook (Automatic Trigger)

To ensure Job 1 runs automatically whenever code is pushed to the dev branch, a GitHub webhook was configured.

### GitHub Webhook Setup:
1. Opened the GitHub repository
2. Navigated to:
   Settings → Webhooks → Add webhook
3. Set the Payload URL to:
   http://<jenkins-public-ip>:8080/github-webhook/
4. Content type set to:
   application/json
5. Selected:
   Push events
6. Saved the webhook

### Jenkins Configuration:
* Enabled **GitHub hook trigger for GITScm polling** in Job 1

![alt text](Job1-image/webhook.png)
### Why this matters:
* Jenkins runs automatically on every push
* No manual “Build Now” required
* Enables true Continuous Integration
### Build Environment:

* Before running the test commands, I enabled Jenkins to use the correct Node.js version by adding Node.js and npm to the PATH.

* This ensures Jenkins can run `npm install` and `npm test` successfully.

![alt text](Job1-image/job1-install_NodeJS.png)

### Build Steps – Running Automated Tests
## Step 6: Add Build Commands
* Under Build Steps, I selected Execute shell and added:
  
cd app
npm install
npm test

![alt text](Job1-image/job1-build_steps.png)

### What this does?:
* Moves into the app folder
* Installs required dependencies
* Runs automated tests
* Followed by clicking save to save your job

### Why this is important:
* If tests fail, the pipeline stops immediately, protecting the production environment.

 ### Running the Job
## Step 7: Build the Job
* After the job has been created, on the left hand side click Build now to run the job.
* Jenkins runs the job automatically
![alt text](Job1-image/job1-ci_test.png)

## Step 8: Checking the Results
* Blue circle ✅ → Tests passed
* Red circle ❌ → Something failed
#### The job will then show under Build history, if the commands have ran successfully it will show a blue circle, however if it has failed I will see a red circle.
 
### I can click Console Output to:
* Confirm successful execution
* See error messages if the build fails
Finally, I can right-click the job and open Console Output to view success messages or errors.

 
 ### Why this is valuable:
* It makes troubleshooting fast and transparent.


#### Outcome of Job 1
### When Job 1 succeeds:
* Code is confirmed working
* The pipeline moves forward to Job 2
* Confidence in deployment increases

### When Job 1 fails:
* Pipeline stops
* No broken code is merged
* Issues are fixed early

### Why This Job Adds Value
 #### For Me
* Less manual testing
* Faster feedback
* Confidence in my code

#### For an Organisation
* Fewer production issues
* Faster release cycles
* Reliable automation
* Better developer productivity

#### Once Job 1 completes successfully, the pipeline allows the workflow to continue to Job 2, where approved changes are merged safely.

