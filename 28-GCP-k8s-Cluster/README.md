# GCP K8s Cluster Setup 

## Please follow the below steps in GCP Console. 
```
	1. Go to GCP Console
	2. Create a new k8s-demo-project
	3. IAM -> Service Account ->  Name: K8s-demo-service-account
	4. Role -> Project -> Editor , Compute Admin , Compute Network Admin
	5. Create Key -> JSON
	6. Enable API -> Kubernetes Engine API
        7. Enable API -> Compute Engine API
```

## Create a JSON Key for your Service Account. 

## Import the same JSON Server Account Key in your terraform Code by refrencing it a key paramter. 
```
# cat kubernetes/providers.tf
provider "google" {
  project = "${var.project_id_map[terraform.workspace]}"
  region  = "${var.region}"
  credentials  = "${file("/root/.ssh/k8s-demo-project-sa.json")}"
  version = "2.19.0"
}
```
