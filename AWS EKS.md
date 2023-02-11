
VPC

API server endpoint access
public and private

Public access source allowlist

-   0.0.0.0/0
    
    (open to all traffic)

subnets public vs private

volume  
storageclass:

gp2

[kafka-high-iops-ssd-csi-us-gov-west-1a](https://console.amazonaws-us-gov.com/eks/home?region=us-gov-west-1#/clusters/k8saas-k8s-1loxl/storageclasses/kafka-high-iops-ssd-csi-us-gov-west-1a)

[kafka-slow-magnetic-us-gov-west-1a](https://console.amazonaws-us-gov.com/eks/home?region=us-gov-west-1#/clusters/k8saas-k8s-1loxl/storageclasses/kafka-slow-magnetic-us-gov-west-1a)


3 subnets
all private
security group  1 inbound , 1 outbound

1 extra secrity group for communication btw api server and nodes.


Authentication:
OIDC provider

Issuer URL

https://confluent.okta.com/oauth2/default

Client ID

0oaao4khck8NMwtH1357

Status

Active

Username claim

sub

Groups claim

groups

Username prefix

okta-user#

Groups prefix

okta-group#

CoreDNS 


Node Group and node
m5-xlarge: 1 group per subnet
main-ppol: 1 group per subnet
ultra: 1 group per subnet

node iam role


CRD:

Webhook:

