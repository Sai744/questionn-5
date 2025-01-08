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

To get the nodes running in the cluster


To  verify all the core components (e.g., kube-apiserver, kube-controller-manager, etc.) are up and running

To see the status of all pods across the entire cluster:

To check all the services running

To check the heck the overall health of your cluster by using the kubectl command to look for the status of the nodes, controllers.

To check the logs of the pods 

