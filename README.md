# cgi-gcp-deploy
## CloudGuard IaaS Google Cloud Platform Deployment Helper
---

### Pre-requisites 

Please do the followings first;

1.  MAKE SURE to update the variables in the script to relfect your actual values. \

2. Make it executable by executing  ```chmod +x cgi-gcp-setup.sh``` 

### Deploy using the script 

It's always a good idea to check if the image is valid.

```bash
gcloud compute images list --project=checkpoint-public | grep check-point-r8040-payg-294-759-v20201202
```

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



Best, \
Jayden AUng