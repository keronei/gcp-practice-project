
# Translation 2
## App Dev: Setting up a Development Environment v1.1

### Ojectives : Learn to;
 - Provision a google compute engine instance
 - Connect to the instance using SSH
 - Install software on the instance
 - Verify the software installation

### Task 1: Creating a Compute Engine Virtual Machine Instance
`$ gcloud compute instances create dev-instance -—zone=us-central1-a -—tags http-server --scopes=https://www.googleapis.com/auth/cloud-platform`

Create a firewall rule for allowing HTTP traffic

`$ gcloud compute firewall-rules create dev-instance-fw-allow-http -—direction=INGRESS -—action=ALLOW -—rules=tcp:80 -—source-ranges=0.0.0.0/0 -—target-tags http-server -—network=default`

SSH into the Instance:
`$ gcloud compute ssh dev-instance`

Reply with `Y` if prompted.

### Task 2: Install software on the VM instance

Update the Debian package
`$ sudo apt-get update`

Install Git
`$ sudo apt-get install git`

Download Node.js setup script
`$ curl -sL https://deb.nodesource.com/setup_6.x | sudo -E bash -`


Install npm and Node.js 
`$ sudo apt install nodejs`


### Task 3: Configure the VM to Run Application Software

Check the node version
`$ node -v`

Clone class repository
`$ git clone https://github.com/GoogleCloudPlatform/training-data-analyst`


Change working directory
`$ cd ~/training-data-analyst/courses/developingapps/nodejs/devenv/`


Run a simple web server
`$ sudo node server/app.js`


Return to the Cloud Console VM instances list, and click on the External IP address for the dev-instance.

Return to the SSH window(cloud shell), and stop the application by pressing Ctrl+C.

Install Node.Js library for compute engine
`$ npm install`

Run a simple Node.js application that lists Compute Engine instance
`$ node list-gce-instances.js`
