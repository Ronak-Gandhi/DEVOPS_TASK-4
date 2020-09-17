# DEVOPS_TASK-4

## TASK OBJECTIVE:-

`1.` **Create container image that’s has Linux and other basic configuration required to run Slave for Jenkins. ( example here we require kubectl to be configured )**

`2.` **When we launch the job it should automatically starts job on slave based on the label provided for dynamic approach**.

`3.` **Create a job chain of job1 & job2 using build pipeline plugin in Jenkins**.

`4.` **Job-1 : Pull the Github repo automatically when some developers push repo to Github and perform the following operations as:**

*  _**Create the new image dynamically for the application and copy the application code into that corresponding docker image**_!

*  _**Push that image to the docker hub (Public repository)**_!

 _( Github code contain the application code and Dockerfile to create a new image )_

`5.` **Job-2 ( Should be run on the dynamic slave of Jenkins configured with Kubernetes kubectl command): Launch the application on the top of Kubernetes cluster performing following operations:**

 * _**If launching first time then create a deployment of the pod using the image created in the previous job. Else if deployment already exists then do rollout of the existing pod making zero downtime for the user**_!

 *  _**If Application created first time, then Expose the application. Else don’t expose it**_!

---

* _**Created container image in which kubernetes also configured from SSH enabled image**_

![Screenshot (183)](https://user-images.githubusercontent.com/64469896/93472031-c0a4af80-f911-11ea-9dc5-1507eb3936d4.png)

* after creating an image by dockerfile ,i pushed it on dockerhub..

* *  _**`JOB-1`.**_ 

![Screenshot (185)](https://user-images.githubusercontent.com/64469896/93474099-8a1c6400-f914-11ea-9a5a-43a78a72747b.png)

![Screenshot (186)](https://user-images.githubusercontent.com/64469896/93474103-8be62780-f914-11ea-9c9d-c9fff601f7a9.png)

![Screenshot (184)](https://user-images.githubusercontent.com/64469896/93474106-8c7ebe00-f914-11ea-9aa9-72fdd30989e3.png)

![Screenshot (187)](https://user-images.githubusercontent.com/64469896/93474137-956f8f80-f914-11ea-97fc-8e1103d5b5c4.png)


* *  _**`JOB-2`.**_ 

_To perform job-2 on cloud,we have to create dynamic slave and configure the dynamic cloud_..
for this ,we have to **append -H tcp://0.0.0.0:4243 to ExecStart in docker.service.file**!!

* **Configue Cloud in jenkins**:-(for this, Docker Plugin should be installed).

![Screenshot (181)](https://user-images.githubusercontent.com/64469896/93491381-40894480-f927-11ea-9559-4927fff8efe0.png)





