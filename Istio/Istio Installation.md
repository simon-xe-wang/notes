## Installation with SPIRE

### Step 1: Install SPIRE

For PoC, just use https://raw.githubusercontent.com/istio/istio/release-1.18/samples/security/spire/spire-quickstart.yaml 
It creates:
1. SPIRE Server
2. SPIRE Controller Manager and 
3. SPIFFE CSI Driver

Reference: annotation about custom template
	- https://istio.io/latest/docs/setup/additional-setup/sidecar-injection/#custom-templates-experimental

### Step 2: Install CRD ClusterSPIFFEID

With ClusterSPIFFEID, we could:
1. set SPIFFEID template
2. enable auto workload registration at namespace or pod level by using selector.

see https://github.com/spiffe/spire-controller-manager/blob/main/docs/clusterspiffeid-crd.md#templates

### Step 3: Install Istio

### Step 4: Register workload

Reference: https://istio.io/v1.14/blog/2019/data-plane-setup/
- Manual injection: 
	- inject init and proxy container's template into targeting pod's template.  
	- Command: `istioctl kube-inject`
- Auto injection:
	- only take effective when creating pod?  mutatingwebhook
	- 3 things could impact if auto injection is enabled on a pod 
		- namespaceSelector in webhook
		- default policy defined in ConfigMap sidecar-injector
		- pod override annotation (sidecar.istio.io/inject)

- Unject sidecar from pod
	- `istioctl x kube-uninject`

### Checking Traffic
Options:
- via iptables
- via Envoy Access logs
- via tcpdump

#### iptables
https://istio.io/v1.14/blog/2019/data-plane-setup/#traffic-flow-from-application-container-to-sidecar-proxy

#### Envoy Access logs
TLS can work without certificates, where it only support encryption and signature.

checking envoy access logs, the cipher it uses is: **TLS_AES_128_GCM_SHA256** 

#### tcpdump

 

### Enable/Disable TLS in Policy PeerAuthentication


## Ingress Gateway

Benefit:
when AWS ALB talking to sidecar of pod directly, it could have 503 issues when a deployment get restarted gracefully, see:
https://domagalski-j.medium.com/aws-alb-returns-503-for-istio-enabled-pods-a6942383143c



## Security 





https://istio.io/latest/docs/concepts/security/#authentication-policies
