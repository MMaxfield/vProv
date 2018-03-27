# Cloud_Lifeguard
VDI Back-end automation

Goal of this project:
Provide a way to handle requests to add, delete or modify virtual desktop resources.

There will be a seperate service responsible for monitoring the availability of resources, vMon. vProv will query vMon to get available resources in order to determine if it can fulfil the provisioning task.

Workflow:
External process sends a request to vProv. vProv calls vInfo for more information and using that additional detail checks vMon to see if resources are available. vMon sends response with available resources that match the vProv request. If the provisioning request is an ADD type, vMon calls vMan to spin up a new machine to the buffer once this provising request is processed. If no resources are available for that request, vMon sends request to vCom to communicate that information to the support team and to the external process.

vProv - External Endpoint
Provisioning Task Handler (add, del, mod)
vInfo
Gathers additional information from Active Directory or other sources.
vMon - External Endpoint
Resource Monitor (Virtual Desktops, CPU, RAM, Hosts, IPs, Active Directory)
vMan
Machine Builder\Destroyer\Changer
vCom
Communication Handler (email, log, syslog, paging)
