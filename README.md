# CloudGuard IaaS (GCP) Deployment Helper Script

This is a simple helper script to automate deploying a specific CloudGuard IaaS gateway image on Google Cloud Platform.

A couple of reasons you might want to do this may include deploying or restoring a Management HA solution or a log server, and restoring a previous backup, etc. 

### Check the exact CloudGuard IaaS image 

Check the CloudGuard images available on Google Cloud.

```bash
gcloud compute images list --project=checkpoint-public 
```

In this lab, we're gonna deploy ```check-point-r8040-payg-294-759-v20201202```.

> You will also need to update the image variable in the script as well.

### Pre-requisites 

Please do the following;

1. Install [Google Cloud SDK](https://cloud.google.com/sdk/docs/install). 

2. A service account with proper permission setup for your GCP Project: https://cloud.google.com/compute/docs/access/service-accounts

3. Enable Compute API: https://cloud.google.com/sdk/gcloud/reference/services/enable

   Example: 
   ```bash 
   gcloud services --project <project name> enable compute.googleapis.com
   ```

4. Download the ```cgi-gcp-setup.sh``` script from this repo, and update the **VARIABLES** in the script. (e.g. project, network, etc)

5. Make the script executable by executing  ```chmod +x cgi-gcp-setup.sh``` 


And Execute the following:

```bash
./cgi-gcp-setup.sh
```

### Expected Output

```bash

./cgi-gcp-setup.sh
WARNING: You have selected a disk size of under [200GB]. This may result in poor I/O performance. For more information, see: https://developers.google.com/compute/docs/disks#performance.
Created [https://www.googleapis.com/compute/v1/projects/helloworld041019/zones/asia-southeast1-a/instances/cg-gateway].
NAME        ZONE               MACHINE_TYPE   PREEMPTIBLE  INTERNAL_IP          EXTERNAL_IP    STATUS
cg-gateway  asia-southeast1-a  n1-standard-2               10.0.0.10,10.4.0.10  35.198.197.18  RUNNING
Your CGI Gateway has been created on Thu Dec 10 13:14:41 +08 2020!

```

### Verify that your Gateway is running

```
$gcloud compute instances list  

NAME            ZONE               MACHINE_TYPE   PREEMPTIBLE  INTERNAL_IP          EXTERNAL_IP    STATUS
cg-gateway      asia-southeast1-a  n1-standard-2               10.0.0.10,10.4.0.10  35.198.197.18  RUNNING
```
---
Reference: [sk163656](https://supportcenter.checkpoint.com/supportcenter/portal?eventSubmit_doGoviewsolutiondetails=&solutionid=sk163656&partition=Advanced&product=CloudGuard)

Best, \
Jayden Aung