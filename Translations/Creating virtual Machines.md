# Translation 1
## LAB: Creating virtual Machines.

### Objectives:
* Explore the available options for VMs and see the differences between locations.

-> Create several standard VMs
-> Create advanced VMs

### Task 1: Create a utility virtual machine

`$ gcloud compute instances create my-linux-vm --machine-type=n1-standard-1 —-zone=us-central1-c —-subnet=default —-no-address`


Explore the VM details:
One can view the details on the cloud shell:
`$ gcloud compute instances describe my-linux-vm --zone=us-central1-c`

Or, click on the virtual machines
Select my-linux-vm
Locate the CPU platform and note the value, Attempt to edit.
Examine Availability Policies
Click on cancel.

Explore the VM Logs
1. On the VM instances details page, click on Stackdriver logging
2. Click the small triangle to the left of one of the lines to see the kind of information it contains.
3. On the far right, click View Options > Expand All

### Task 2: Create a windows virtual machine
First check the available images
`$gcloud compute images list`

Proceed to creating a machine using Windows Server 2016 Datacenter Core

`$ gcloud compute instances create my-windows-vm --zone=europe-west2-a --machine-type=n1-standard-2 --image-project=windows-cloud --image=windows-server-2016-dc-v20200813 --boot-disk-type pd-ssd  --boot-disk-size=100GB --tags http-server, https-server`

Create Firewall to allow HTTP & HTTPS traffic

`$ gcloud compute firewall-rules create my-windows-fw-allow-http --direction=INGRESS --action=ALLOW --rules=tcp:80  --source-ranges=0.0.0.0/0 --target-tags http-server —-network=default`

`$ gcloud compute firewall-rules create my-windows-fw-allow-https —-direction=INGRESS —-action=ALLOW —network=default —rules=tcp:443 —-source-ranges=0.0.0.0/0 —-target-tags https-server` 

Set the password for the windows VM
	1	Click on the name of your Windows VM to access the VM instance details.
	2	You don't have a valid password for this Windows VM: you cannot log in to the Windows VM without a password. Click Set Windows password.
	3	Click Set.
	4	Copy the provided password, and click CLOSE.  

### Task 3: Create a custom virtual machine
`$ gcloud compute instances create my-custom-vm —-zone us-west1-b --custom-cpu 6 —-custom-memory 32`

Connect via ssh to custom VM
`$ gcloud compute ssh my-custom-vm`

Reply with `Y` if prompted.

To see info about memory consumption and swap:
`$ free`

To see details about he RAM installed:
`$ sudo dmidecode -t 17`

To verify number of processors:
`$ nproc`

To see details about the CPU installed on the VM:
`$ lscpu`

To exit:
`$ exit` 



