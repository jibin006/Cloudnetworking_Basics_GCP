# Cloudnetworking_Basics
30 days challenge to specialize in cloud networking_GCP 

Day 1: GCP Cloud Networking – VPC & Basic Networking
1.	Introduction to GCP:
o	Learned about Google Cloud Platform (GCP) as a cloud service provider.
o	GCP offers scalable infrastructure with services like compute, storage, and networking.
2.	Virtual Private Cloud (VPC):
o	A VPC is a virtual network in GCP that isolates and manages cloud resources.
o	Key components:
	Subnets: Segments of a VPC with defined IP ranges in specific regions.
	Firewall Rules: Control inbound and outbound traffic to resources.
	IP Addressing: Differentiated between internal (private) and external (public) IPs.
3.	Hands-On Tasks:
o	Set up a GCP account and enabled Compute Engine.
o	Created a VPC and configured custom subnets using CIDR blocks.
o	Set up basic firewall rules to manage network traffic.
o	Created two VM instances in the VPC and tested internal connectivity between them using ping.

Day 2: In-Depth Understanding of Virtual Private Clouds (VPC)
1.	VPC Overview:
o	VPC (Virtual Private Cloud): Isolated, private networks in GCP that enable resource control and network management.
o	Default VPC: Automatically created by GCP with pre-configured subnets in each region. Easy to use but lacks customization.
o	Custom VPC: Manually configured, allowing more control over subnets, regions, IP ranges, and firewall rules for better security and network segmentation.
2.	Key Components:
o	Subnets: Define IP ranges within regions.
o	Firewall Rules: Control ingress and egress traffic to and from resources.
o	CIDR Blocks: Non-overlapping IP ranges are required for VPCs to ensure proper routing.
3.	VPC Peering:
o	Allows private communication between two VPCs.
o	Important to ensure non-overlapping IP ranges and proper firewall rules.
o	Requires mutual acceptance of the peering connection by both VPCs.
o	Need to configure routes and firewall rules for communication.
4.	Hands-On Tasks:
o	Created multiple custom VPCs with different CIDR ranges.
o	Explored default VPC and created new custom VPCs to understand the differences.
o	Tested network isolation between VPCs.
o	Set up VPC Peering to enable communication between two custom VPCs.

Day 3: Subnets – Regional and Zonal Scope
1.	Subnets Overview:
o	Subnets are subdivisions of a VPC that define IP address ranges and serve as a foundation for networking in GCP.
o	Subnets are regional, meaning they are available across all zones in a region.
2.	Regional vs. Zonal Resources:
o	Subnets themselves are regional, but VMs and other resources are zonal, tied to specific zones within a region.
o	To simulate zonal subnets, you can create multiple subnets in the same region with different IP ranges and assign resources in different zones to these subnets.
3.	Hands-On Tasks:
o	Created multiple subnets in the same region (us-central1), each with distinct IP ranges.
o	Assigned VMs to specific zones (us-central1-a, us-central1-b), each using a different subnet.
o	Tested connectivity and learned how regional subnets can span multiple zones while resources (like VMs) are assigned to specific zones.

Subnet >> Region >> Zone >> VM

Day 4: Firewalls – Concepts and Best Practices
1.	Firewall Basics:
o	Firewall rules control ingress (incoming) and egress (outgoing) traffic in GCP.
o	GCP firewall rules are stateful, meaning they automatically allow return traffic.
2.	Ingress vs. Egress:
o	Ingress Rules: Manage incoming traffic to VMs, such as allowing SSH or HTTP.
o	Egress Rules: Control outgoing traffic from VMs, like blocking internet access.
3.	Firewall Targeting:
o	Tags or Service Accounts are used to apply rules to groups of VMs dynamically, instead of manually specifying IP addresses.
4.	Hands-On Tasks:
o	Configured an ingress rule to allow SSH (port 22) access.
o	Configured an egress rule to block internet access for VMs.
o	Enabled firewall logging to monitor allowed and denied traffic.

Day 5: Stateful vs. Stateless Firewall Rules & Secure VPC Setup
1.	Stateful vs. Stateless Firewalls:
o	Stateful: GCP’s default, where return traffic is automatically allowed for permitted traffic.
o	Stateless: Requires explicit rules for both incoming and outgoing traffic, providing more granular control.
2.	Secure VPC Setup:
o	Created a VPC and applied the principle of least privilege.
o	Configured deny-all ingress and egress rules as defaults.
o	Created allow rules for specific services (SSH, HTTP/HTTPS) with lower priority than the deny rule.
o	Ensured allow rules are processed first by assigning lower priority values

Day 6: Routes and Routing Tables – Static and Dynamic Routing
1.	Routes and Routing Tables:
o	Routes define paths for traffic within and outside a VPC.
o	Routing tables manage collections of routes to control network traffic flow.
2.	Types of Routes:
o	Static Routes: Manually configured, suitable for simple, fixed routing needs.
o	Dynamic Routes: Automatically managed by Cloud Router to update routes in real-time, ideal for hybrid or frequently changing networks.
3.	Default Routing:
o	GCP creates default routes for internal traffic within the VPC and internet access (0.0.0.0/0).
4.	Hands-On Tasks:
o	Explored default routes in a VPC.
o	Created a static route to direct traffic via a custom gateway.
o	Set up a Cloud Router for dynamic routing to manage route updates automatically.

Day 7: Cloud NAT – Concepts and Configuration
1.	Cloud NAT Overview:
o	Enables private instances (without external IPs) to securely access the internet for outbound connections.
o	Prevents inbound internet connections, enhancing security.
2.	Setup:
o	Created a Cloud Router and configured a NAT Gateway for the VPC.
o	Enabled NAT for private subnets to allow outbound internet access.
3.	Testing:
o	Verified internet access from a VM without an external IP using Cloud NAT.
o	Monitored traffic and NAT activity in the Logs Explorer.

Day 8: VPC Peering – How it Works and Configuration
1.	VPC Peering Overview:
o	Allows private communication between two VPC networks in GCP over Google’s internal network.
o	Requires non-overlapping IP ranges and provides low-latency, secure connections.
2.	Configuration:
o	Created two VPCs (vpc-a and vpc-b) with unique CIDR ranges.
o	Set up bidirectional peering connections and configured firewall rules for ICMP and SSH.
3.	Testing:
o	Verified connectivity by pinging between VMs in each VPC using private IPs, confirming the peering setup.

Day 9: Shared VPCs – Centralizing Network Resources
1.	Shared VPC Overview:
o	Allows multiple projects to share a single VPC for centralized network management.
o	Host Project manages the network, while Service Projects use shared subnets.
2.	Configuration:
o	Set up a host project with shared subnets and assigned a service project to use them.
o	Configured roles: Shared VPC Admin for the host project, Network User for the service project.
3.	Verification:
o	Created a VM in the service project using the shared subnet, confirming connectivity.

Day 10: VPNs – Hybrid Connectivity Setup
Cloud VPN Overview:

Enables secure, encrypted connections between on-premises networks and GCP VPCs.
Uses IPsec encryption and supports both standard and HA (High Availability) VPN options.
Configuration:

Set up a Cloud VPN Gateway and VPN Tunnel in GCP.
Configured routing (static or dynamic with BGP) and firewall rules to allow VPN traffic.
Verification:

Tested connectivity from on-prem to GCP by pinging or SSHing into GCP VMs, confirming secure hybrid connectivity.


<img width="335" alt="image" src="https://github.com/user-attachments/assets/ccc72171-a930-472e-84d9-78e3f4ff3e54">

Day 11: HA VPN – High Availability VPN Setup
HA VPN Overview:

High Availability VPN provides a 99.99% SLA for reliable, resilient VPN connections.
Uses dual tunnels and supports BGP for automatic failover and dynamic routing.
Configuration:

Set up an HA VPN Gateway with two interfaces for redundancy.
Configured dual tunnels connecting GCP to the on-premises network for high availability.
Verification:

Tested failover by disabling one tunnel and confirming seamless traffic flow through the second tunnel.

Day 12: GCP Load Balancers – HTTP(S) Load Balancer Setup
Load Balancer Overview:

Distributes incoming traffic across instances to improve availability, reliability, and scalability.
HTTP(S) Load Balancer supports global reach, SSL termination, and path-based routing.
Configuration:

Created an instance group for backend services.
Set up an HTTP(S) Load Balancer with frontend IP, backend group, health checks, and URL mapping.
Testing:

Accessed the load balancer’s IP to verify traffic distribution across instances.




