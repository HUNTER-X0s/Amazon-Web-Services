# Amazon EKS: Console Walkthrough

**Mental model:** EKS manages the Kubernetes control plane; you still choose cluster networking, identity, add-ons, and compute capacity. A cluster is not just a button—its networking, EC2 nodes/Fargate, load balancers, and storage can all bill separately.

Related note: [KUBERNETES.md](../../KUBERNETES.md)

## Plan before using the console

- Use a dedicated sandbox account and check current EKS, EC2, NAT Gateway, load balancer, and data-transfer pricing. A running cluster can become expensive quickly.
- Prepare a VPC/subnets across Availability Zones, cluster IAM role, node role or EKS Auto Mode configuration, and a supported Kubernetes version.
- For a first console exercise, review the current [EKS Auto Mode quick configuration](https://docs.aws.amazon.com/eks/latest/userguide/automode-get-started-console.html); it provisions more automatically. Use custom configuration only to learn the components explicitly.

## Create a learning cluster

1. Open [Amazon EKS](https://console.aws.amazon.com/eks/home#/clusters), choose the Region, then **Add cluster → Create**.
2. Choose quick or custom configuration. Enter a cluster name and supported Kubernetes version.
3. Choose the cluster IAM role and VPC. Use private subnets for worker nodes where practical; review endpoint access (public/private), allowed CIDRs, logging, encryption, and add-ons.
4. Select capacity: EKS Auto Mode, managed node groups, Fargate profiles, or another supported option. For a managed node group, choose node role, instance types, desired/min/max counts, and private subnets.
5. Review add-ons, tags, access entries, and estimated capacity. Create the cluster and wait for **Active**.
6. Use **Connect** or the documented AWS CLI/kubectl setup to access it. Deploy only a harmless test workload and verify node and pod state.

## Clean up completely

Delete test Kubernetes services and load balancers first. Then delete node groups/Fargate profiles, add-ons as appropriate, and the EKS cluster. Remove EKS-created security groups, ENIs, NAT gateways, and CloudFormation stacks only after confirming ownership and dependency. Check EC2, ELB, VPC, and billing pages afterward.

**Remember:** **control plane + compute + network + Kubernetes access** all matter.

**Official references:** [Get started with EKS using the console](https://docs.aws.amazon.com/eks/latest/userguide/getting-started-console.html) · [Create a cluster](https://docs.aws.amazon.com/eks/latest/userguide/create-cluster.html)
