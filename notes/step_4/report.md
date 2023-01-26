# Node elasticity

1. When I have deployed the bloaty-mcbloatface deployment, there were pods in Pending state
![cluster_1](screenshoot/bloaty-mcbloatface_pods_pending_state.png)

2. I have described one pod in Pending state and I saw that it is a space problem and I need to deploy more VM. 
![cluster_2](screenshoot/bloaty-mcbloatface_deployment_failed.png)

We have decided to scale out that is the option cheaper than increase the size of nodes. 

3. I created an autoscaling group to trigger increases to VM's in the autoscaling group 
I create an autoscaling group with *cluster_autoscale.yml* file, that I have added this file in the bloatware file

4. I have created a node autoscaling configuration:
* Setup OIDC provider
![cluster_3](screenshoot/setup_oidc_provider.png)

* Create a cluster sevice account with IAM permissions
![cluster_4](screenshoot/cluster_service_account_with_iam_permission.png)

* I checked the CloudFormation cluster-autoscaler stack is in created state
![cluster_5](screenshoot/cloudformation_cluster-autoscaler_stack_created.png) 

5. In console, have checked:
* The number of EC2 instances is two
![cluster_6](screenshoot/bloaty-mcbloatface_2_instances_before.png)

* The size of autoscaling group before to do the changes
![cluster_7](screenshoot/bloaty-mcbloatface_auto_scaling_group_before.png)

6. I have fixed the fail to increase the size of the autoscaling group.
I have changed:
* nodes_max_size     = 3
* nodes_min_size     = 2

![cluster_8](screenshoot/auto_scaling_group_size_changed.png)

7. I have updated the infrastructure with *terraform apply*

8. I deployed the cluster-autoscale
![cluster_9](screenshoot/cluster-autoscaler_created.png)

9. I see that all 17 bloaty-mcbloatface pods are in Running state
![cluster_10](screenshoot/node-elasticity_bloaty-mcbloatface_running.png)

10. I see that increase the number of nodes to 3
![cluster_11](screenshoot/after_fix_error_increase_number_nodes.png)
