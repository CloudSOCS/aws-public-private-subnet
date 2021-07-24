AWS Puiblic and Private Subnets
---

![network](/pics/network.jpg)

So if you read the Intro to VPC in AWS, you saw that there are some subnets in there and those subnets were public subnets.

Sometimes we want our resources to be private and we don't want them to have public addresses. So we need to understand how to configure our subnets.

![diagram](/pics/subnet1.png)

We have two subnets, one is a private subnet and one's a public subnetand we've launched two EC2 instances, one into each subnet and both of these will have a private IP address, and will be from the subnet range assigned to that particular subnet. We have a CIDR block, which is an IPv4 block of addresses that we use for our VPC and then our subnets have a range of addresses from within the CIDR block.Our EC2 instances will always have a private IP address from that range.

![sub gateway](/pics/2.png)

You have to have a public IP assigned to use an Internet gateway directly.
Now, if we have the private subnet route table, which is associated with this private subnet,it will also have an entry for local, which means that the instances can communicate amongst themselves between the subnets without a problem using the implicit router. But if you want to send them to the outside world,they can't do that via an Internet gateway.They need to use a different device called a NAT gateway. A NAT gateway gets put into a public subnet and then the instance communicates via the NAT gateway,which in turn goes to the Internet gateway and out to the Internet.

So the public subnet will have the auto assigned IP addresses set to yes.It will also have a subnet route table that has a route to an Internet gateway.
Private subnet instances do not have a public IP.They also don't have a route to an Internet gateway and they must use a NAT gateway if they want to access the Internet.
