# intro-to-AWS-VPC

Head to networking and content delivery, choose VPC, and we can now see the resources

![1.pmg](/pics/1.png)

![2.png](/pics/2.png)

This is a region specific service.In the top right hand corner, we can see N.Virginia.

We can see the number of VPCs, the number of subnets, in this case, I have one
route tables and I have one, Internet gateways.

When you create your account it automatically creates a VPC in every region And it creates a subnet, which is going to be a public subnet, which means it will have public IP addresses for your resources.
In US-North Virginia, there are six availability zones, so we have six subnets, whereas in Sydney there are three availability zones so there are three subnets.

Now if go to your VPCs on the left, We have the VPC ID and we can see the IPv4 CIDR block and it doesn't have an IPv6 CIDR block by default.

![3.png](/pics/3.png)

If we go to subnets

![4.png](/pics/4.png)

we can see all six subnets and each of these will have an IPv4 network address that's part of, it's a subset of the IPv4 CIDR block range associated to the VPC.

If we scroll across a little, we can see the available IP for addresses.

![5.png](/pics/5.png)

So we get 4,091 IPv4 addresses that we can use.

So by default, a route table is created known as the main route table.


They also have a network ACL, which is a security technology.It's basically a firewall operating at the subnet level

![6.png](/pics/6.png)

So that means if we launched an EC2 instance into one of these subnets by default, it would get an IPv4 public IP address and it would be accessible on the Internet.

Let's go to route tables and see how the route table is configured.

![7.png](/pics/7.png)

We have one route table and in the bottom box we've got some information. Choose routes and we can see what's configured by default.
We got the IPv4 CIDR block with a target of local.

![9.png](/pics/9.png)

The router in the VPC is going to allow all traffic.So any of those subnets we've got various ranges,So if you were trying to talk from any one of those IPv4 ranges, these different subnets to any other subnet in that overall address range,then the implicit router is going to route that connection.


We also we have the IPv4 any address. 0.0.0.0/0 means any other address,So if it's not an address within this range, it's an address within this range and therefore it will go to this particular device.

Now go to Internet gateways.

![10.png](/pics/10.png)

Internet gateways are attached to your VPC you can use them when you have a target in your route table to be able to send data out to the Internet.Your EC2 instances will also need public IP addresses in order to be able to use the Internet gateway and talk on the Internet. An egress only Internet gateway is for IPv6.

So that's all for now I wanted to show you around and get familiar. Next I will show you how to start creating VPCs on AWS.
