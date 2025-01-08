* To provision an Amazon Elastic Kubernetes Service (EKS) cluster using Terraform, you will need to create a script that includes several key components such as:
1.AWS Provider: To interact with AWS resources.
2.VPC: The Virtual Private Cloud (VPC) where the EKS cluster will be created.
3.EKS Cluster: The EKS cluster itself.
4.EKS Node Group: The worker nodes that run the Kubernetes workloads.
5.IAM Roles and Policies: For EKS to interact with AWS services and manage resources.
I have created vpc, sg . Please refer to that github URL.
There are .tf files to create an eks cluster. It includes main.tf, variables.tf, locals.tf, parameters.tf, provider.tf files.

Here iam using AWS provider. Provider configuration is mandatory inorder to run the terraform configuration code.
When we give terraform init terraform searches for the provider configuaration in provider.tf files and downloads the required provider configuration.

Aws_key_pair --> creates SSH keypair in AWS which you can use to access the ec2 instances.
Module eks --> here iam using terraform eks inbuilt module
Cluster name, version --> sets the eks cluster name and the version of the cluster

We also need to give vpc id , sg id and node sg ids etc inorder to configure the cluster properly.
eks_managed_node_group_defaults: This sets default instance types for the managed node groups. It specifies a list of EC2 instance types (m6i.large, m5.large, etc.) that the worker nodes can use.
eks_managed_node_groups: Defines specific managed node groups, in this case, a green node group.

For EKS, you can configure your kubectl to use the EKS cluster by running the following command:

![80](https://github.com/user-attachments/assets/5bac3c45-1e5f-445a-b8c3-bd507e6fd8f4)

To get the nodes running in the cluster

![81](https://github.com/user-attachments/assets/cfbfb3ff-7006-425b-a983-c5521381350c)

To  verify all the core components (e.g., kube-apiserver, kube-controller-manager, etc.) are up and running

![82](https://github.com/user-attachments/assets/696ea7a3-2573-44e8-b8f4-476f874f8e72)

To see the status of all pods across the entire cluster:

![83](https://github.com/user-attachments/assets/19fac513-5d9b-471c-b264-64f28e0f5ce5)

To check all the services running

![84](https://github.com/user-attachments/assets/0d6719fd-ef85-4fde-af6f-3b3142915a32)

To check the overall health of your cluster by using the kubectl command to look for the status of the nodes, controllers.

![85](https://github.com/user-attachments/assets/b042f0ca-51a5-48d6-a0c9-12b1b92688b1)

To check the logs of the pods 

![86](https://github.com/user-attachments/assets/73c95be3-450f-42b0-b569-eafef95e2acb)

