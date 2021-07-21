

![CloudSOC logo](https://1.bp.blogspot.com/-YaqntajfnjI/YPcbjtDTuRI/AAAAAAAAAH4/PPe7LLbuo6sipM1cWVIT5FdBC7wzPG54gCLcBGAsYHQ/s150/cloudsoc.png)

Introduction to AWS VPC
-----------

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

Public and Private Subnets
------------------------

![network](/pics/network.jpg)

So if you read the Intro to VPC in AWS, you saw that there are some subnets in there and those subnets were public subnets.

Sometimes we want our resources to be private and we don't want them to have public addresses. So we need to understand how to configure our subnets.

![diagram](/pics/diagram.png)

We have two subnets, one is a private subnet and one's a public subnetand we've launched two EC2 instances, one into each subnet and both of these will have a private IP address, and will be from the subnet range assigned to that particular subnet. We have a CIDR block, which is an IPv4 block of addresses that we use for our VPC and then our subnets have a range of addresses from within the CIDR block.Our EC2 instances will always have a private IP address from that range.

You have to have a public IP assigned to use an Internet gateway directly.
Now, if we have the private subnet route table, which is associated with this private subnet,it will also have an entry for local, which means that the instances can communicate amongst themselves between the subnets without a problem using the implicit router. But if you want to send them to the outside world,they can't do that via an Internet gateway.They need to use a different device called a NAT gateway. A NAT gateway gets put into a public subnet and then the instance communicates via the NAT gateway,which in turn goes to the Internet gateway and out to the Internet.

So the public subnet will have the auto assigned IP addresses set to yes.It will also have a subnet route table that has a route to an Internet gateway.
Private subnet instances do not have a public IP.They also don't have a route to an Internet gateway and they must use a NAT gateway if they want to access the Internet.
