# Blue-green deployments

1. I have checked in the pods that there are only pods from blue deployments
![blue-green_1](screenshoot/blue_pods_before_blue-green_deploy.png)

2. I have created the green service to deploy in terraform, the name of this profile is green.yml. Also I have added in the profile dns.tf another DNS CNAME record resource for the green deployment. I have defined the same weight like blue in this new record because I need 50% blue and 50% green deployment

3. I have launched blue-green.sh to deploy green deployment
![blue-green_2](screenshoot/blue-green_deploy_and_blue-svc.png)

4. I have deployed another time the terraform infraestructure with the command: terraform apply

5. I have checked that we have deployed blue and green environment
![blue-green_3](screenshoot/pods_blue_and_green_after_deploy.png)

6. I have checked in Route 53 that we have the two CNAME records blue and green:
![blue-green_4](screenshoot/route_53_CNAME_blue_and_green_record.png)

* blue:
![blue-green_5](screenshoot/route_53_CNAME_blue_record.png)

* green:
![blue-green_6](screenshoot/route_53_CNAME_green_record.png)

7. I have checked that the 2 Load Balancer have been created for blue and green deployment.
![blue-green_7](screenshoot/load_balancer_blue_and_green.png)

8. In the curl-instance I have curl the blue-green.udacityproject with the result 50% blue and 50% green.
![blue-green_8](screenshoot/blue-green.png)

9. I have removed in Route 53 the CNAME blue record
![blue-green_9](screenshoot/route_53_remove_CNAME_blue_record.png)

10. In curl-instance I have curl the blue-green.udacityproject with the result only green.
![blue-green_10](screenshoot/green-only.png)
