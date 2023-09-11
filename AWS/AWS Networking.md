## Security Group
[[Security Group]] is a virtual fire wall
[[Security Group]] is associated with a network interface instead of EC2 instance.
Each EC2 instance has a default network interface, which has a Security Group associated.

Subnet Isolation is achived by Security Group

Example:
2 subnets, 
- subA: 10.0..0.0/25,
- subB: 10.0.0.128/25
Use SG to limit only instances within a subnet can talk to each other. But across subnets can't.


VPC ACL vs Security Group
- ACL is at VPC level.

## Elastic IP
EIP vs Public IP
- EIP is static 
- public IP will be lost when an instance restarts.
EIP could be attached to Default eth0

## ENI
with ENI, it's ENI associated with a subnet instead of EC2 instance. 

2 use cases:
- failover: one ENI could be dynamically attached to any EC2 instance
- one instance could have multiple ENIs so attached to multi subnets. e.g., public and private subnets.

## VPC Endpoint
which is a Endpoint Network Interface
for instances and applications in a subnet to access AWS public services. 





