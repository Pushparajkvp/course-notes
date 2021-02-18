# Nova related notes

## OpenStack Compute API

1. Introduction
    1. [API Doc](https://docs.openstack.org/api-guide/compute/index.html)
    1. The nova project has a RESTful HTTP service called the OpenStack Compute API.
    1. Depending on the deployment those compute resources might be Virtual Machines, Physical Machines or Containers.
    1. It contains both
        1. End User APIs
        1. Operator APIs
    1. It works with Keystone and oslo.policy to deliver RBAC(Role-Based Access Control)
    1. API versions,
        1. /     - Lists all available versions
        1. /v2   - Compute API 2.0
        1. /v2.1 - Same API, except uses microservices
1. Users
    1. Keystone middleware is used to authenticate users and identify their roles.
    1. we should standardize on the following types of user:
        1. application deployer: creates/deletes servers, directly or indirectly via API
        1. application developer: creates images and applications that run on the cloud
        1. cloud administrator: deploys, operates and maintains the cloud
    1. But there will be much wider usecases in real time implementation and they can also be addressed
1. Versions
    1. URI versioning scheme
        1. The first element of the path contains the target version identifier 

        ```http
        GET /v2.1/214412/images HTTP/1.1
        Host: servers.api.openstack.org
        Accept: application/json
        X-Auth-Token: eaaafd18-0fed-4b3a-81b4-663c99ec1cbb
        ```

    1. Mime type versionig scheme
        1. The MIME type versioning scheme uses HTTP content negotiation where the Accept or Content-Type headers contains a MIME type that identifies the version (application/vnd.openstack.compute.v2.1+json).
        1. A version MIME type is always linked to a base MIME type, such as application/json.

        ```http
        GET /214412/images HTTP/1.1
        Host: servers.api.openstack.org
        Accept: application/vnd.openstack.compute.v2.1+json
        X-Auth-Token: eaaafd18-0fed-4b3a-81b4-663c99ec1cbb
        ```

    1. If conflicting versions are specified using both an HTTP header and a URI, the URI takes precedence.
    1. Permanent Links
        1. The MIME type versioning approach allows for creating of permanent links, because the version scheme is not specified in the URI path
        1. If a request is made without a version specified in the URI or via HTTP headers, then a multiple-choices response (300) follows that provides links and MIME types to available versions.
        1. CURRENT -> latest
        1. SUPPORTED -> Old
        1. DEPRECATED -> not supported
        1. EXPERIMENTAL -> In development

        ```json
        {
            "choices": [
                {
                    "id": "v2.0",
                    "links": [
                        {
                            "href": "http://servers.api.openstack.org/v2/7f5b2214547e4e71970e329ccf0b257c/servers/detail",
                            "rel": "self"
                        }
                    ],
                    "media-types": [
                        {
                            "base": "application/json",
                            "type": "application/vnd.openstack.compute+json;version=2"
                        }
                    ],
                    "status": "SUPPORTED"
                },
                {
                    "id": "v2.1",
                    "links": [
                        {
                            "href": "http://servers.api.openstack.org/v2.1/7f5b2214547e4e71970e329ccf0b257c/servers/detail",
                            "rel": "self"
                        }
                    ],
                    "media-types": [
                        {
                            "base": "application/json",
                            "type": "application/vnd.openstack.compute+json;version=2.1"
                        }
                    ],
                    "status": "CURRENT"
                }
            ]
        }
        ```

1. Microversions
    1. API v2.1 supports microversions: small, documented changes to the API
    1. There are multiple cases which you can resolve with microversions:
        1. Older clients with new cloud, Before using an old client to talk to a newer cloud, the old client can check the minimum version of microversions to verify whether the cloud is compatible with the old API. This prevents the old client from breaking with backwards incompatible API changes.
        1. User discovery of available features between clouds, The new features can be discovered by microversions. The user client should check the microversions firstly, and new features are only enabled when clouds support. In this way, the user client can work with clouds that have deployed different microversions simultaneously.
    1. Version Discovery
        1. The Version API will return the minimum and maximum microversions.
        1. Requests to / will get version info for all endpoints. A response would look as follows:

        ```json
        {
            "versions": [
                {
                    "id": "v2.0",
                    "links": [
                        {
                            "href": "http://openstack.example.com/v2/",
                            "rel": "self"
                        }
                    ],
                    "status": "SUPPORTED",
                    "version": "",
                    "min_version": "",
                    "updated": "2011-01-21T11:33:21Z"
                },
                {
                    "id": "v2.1",
                    "links": [
                        {
                            "href": "http://openstack.example.com/v2.1/",
                            "rel": "self"
                        }
                    ],
                    "status": "CURRENT",
                    "version": "2.14",
                    "min_version": "2.1",
                    "updated": "2013-07-23T11:33:21Z"
                }
            ]
        }
        ```

    1. Client Interaction
        1. A client specifies the microversion of the API they want by using the following HTTP header:

        ```http
        X-OpenStack-Nova-API-Version: 2.4
        ```

        1. This acts conceptually like the “Accept” header. Semantically this means:
            1. If neither X-OpenStack-Nova-API-Version nor OpenStack-API-Version (specifying compute) is provided, act as if the minimum supported microversion was specified.
            1. If both headers are provided, OpenStack-API-Version will be preferred.
            1. If X-OpenStack-Nova-API-Version or OpenStack-API-Version is provided, respond with the API at that microversion. If that’s outside of the range of microversions supported, return 406 Not Acceptable.
            1. If X-OpenStack-Nova-API-Version or OpenStack-API-Version has a value of **latest** (special keyword), act as if maximum was specified.
1. Key Compute API Concepts
    1. OpenStack Compute is a compute service that provides server capacity in the cloud
    1. Concepts
        1. Server
            1. A virtual machine (VM) instance, physical machine or a container in the compute system. 
            1. Flavor and image are requisite elements when creating a server. A name for the server is also required.
        1. Flavor
            1. Virtual hardware configuration for the requested server.
            1. Each flavor has a unique combination of disk space, memory capacity and priority for CPU time.
        1. Flavor Extra Specs
            1. Key and value pairs that can be used to describe the specification of the server which is more than just about CPU, disk and RAM.
        1. Image
            1. A collection of files used to create or rebuild a server.
            1. You may also create custom images from cloud servers you have launched.
        1. Image Properties
            1. Key and value pairs that can help end users to determine the requirements of the guest operating system in the image.
        1. Key Pair
            1. An ssh or x509 keypair that can be injected into a server at it’s boot time.
            1. This allows you to connect to your server once it has been created without having to use a password.
            1. If you don’t specify a key pair, Nova will create a root password for you, and return it in plain text in the server create response.
        1. Volume
            1. A block storage device that Nova can use as permanent storage.
            1. When a server is created it has some disk storage available, but that is considered ephemeral, as it is destroyed when the server is destroyed.
            1. A volume can be attached to a server, then later detached and used by another server.
            1. Volumes are created and managed by the Cinder service.
        1. Quotas
            1. An upper limit on the amount of resources any individual tenant may consume.
            1. Quotas can be used to limit the number of servers a tenant creates, or the amount of disk space consumed, so that no one tenant can overwhelm the system and prevent normal operation for others.
        1. Rate Limiting
            1. Accounts may be pre-configured with a set of thresholds (or limits) to manage capacity and prevent abuse of the system.
            1. The system recognizes absolute limits. Absolute limits are fixed
        1. Availability zone
            1. A grouping of host machines that can be used to control where a new server is created.
            1. This is different from AWS "Availability zone" because this is not grouping by geographical zones
    1. Networking Concepts
        1. Networking is handled by Neutron!
        1. The most important networking resource is a port which is part of a network
        1. Ports can have security groups applied to control firewall access.
        1. Ports can also be linked to floating IPs for external network access depending on the networking service configuration.
            1. Floating IP address is a normal IP address assigned to a server which might fail in some circumstances and its IP will be taken by a redundant server which runs alongside with the failed server and serves the clients on behalf of it.
            1. The delivery of packets to the interface with the assigned floating address is the responsibility of Neutron's L3 agent.
        1. When creating a server or attaching a network interface to an existing server, zero or more networks and/or ports can be specified to attach to the server.
        1. If nothing is provided, the compute service will by default create a port on the single network available to the project making the request.
        1. If more than one network is available to the project, such as a public external network and a private tenant network, an error will occur and the request will have to be made with a specific network or port.
    1. Administrator Concepts
        1. Services
            1. Services are provided by Nova components.
            1. Normally, the Nova component runs as a process on the controller/compute node to provide the service.
            1. The status of each service is monitored by Nova, and if it is not responding normally, Nova will update its status so that requests are not sent to that service anymore.
            1. The service can also be controlled by an Administrator
            1. nova-osapi_compute
                1. This service provides the OpenStack Compute REST API to end users and application clients.
            1. nova-metadata
                1. This service provides the OpenStack Metadata API to servers. The metadata is used to configure the running servers.
            1. nova-scheduler
                1. This service provides compute request scheduling by tracking available resources, and finding the host that can best fulfill the request.
            1. nova-conductor
                1. This service provides database access for Nova and the other OpenStack services, and handles internal version compatibility when different services are running different versions of code.
                1. The conductor service also handles long-running requests.
            1. nova-compute
                1. This service runs on every compute node, and communicates with a hypervisor for managing compute resources on that node.
        1. Services Actions
            1. The services actions described in this section apply only to nova-compute services.
            1. enable, disable, disable-log-reason
                1. The service can be disabled to indicate the service is not available anymore. This is used by administrator to stop service for maintenance.
                1. For example, when Administrator wants to maintain a specific compute node, Administrator can disable nova-compute service on that compute node.
                1. Then nova won’t dispatch any new compute request to that compute node anymore.
            1. forced-down
                1. This action allows you set the state of service down immediately.
        1. Hosts
            1. Hosts are the physical machines that provide the resources for the virtual servers created in Nova.
            1. They run a hypervisor that handles the actual creation and management of the virtual servers.
            1. Hosts also run the Nova compute service, which receives requests from Nova to interact with the virtual servers on that machine.
            1. When compute service receives a request, it calls the appropriate methods of the driver for that hypervisor in order to carry out the request.
            1. The driver acts as the translator from generic Nova requests to hypervisor-specific calls.
            1. Hosts report their current state back to Nova, where it is tracked by the scheduler service, so that the scheduler can place requests for new virtual servers on the hosts that can best fit them.
        1. Host Actions
            1. A host action is one that affects the physical host machine, as opposed to actions that only affect the virtual servers running on that machine.
            1. There are three ‘power’ actions that are supported: startup, shutdown, and reboot.
            1. There are also two ‘state’ actions: enabling/disabling the host, and setting the host into or out of maintenance mode.
        1. Hypervisors
            1. A hypervisor, or virtual machine monitor (VMM), is a piece of computer software, firmware or hardware that creates and runs virtual machines.
            1. In nova, each Host runs a hypervisor. Administrators are able to query the hypervisor for information, such as all the virtual servers currently running, as well as detailed info about the hypervisor, such as CPU, memory, or disk related configuration.
            1. Currently nova-compute also supports Ironic and LXC, but they don’t have a hypervisor running.
        1. Aggregates
            1. Host aggregates are a mechanism for partitioning hosts in an OpenStack cloud, or a region of an OpenStack cloud, based on arbitrary characteristics. 
            1. Examples where an administrator may want to do this include where a group of hosts have additional hardware or performance characteristics.
    1. Server Concepts
        1. For the OpenStack Compute API, a server is a virtual machine (VM) instance, a physical machine or a container.
        1. Server Status
            1. Server contains a status attribute that indicates the current server state.
            1. ACTIVE: The server is active.
            1. BUILD: The server has not yet finished the original build process.
            1. DELETED: The server is deleted.
            1. ERROR: The server is in error.
            1. HARD_REBOOT: The server is hard rebooting. This is equivalent to pulling the power plug on a physical server, plugging it back in, and rebooting it.
            1. MIGRATING: The server is migrating. This is caused by a live migration (moving a server that is active) action.
            1. PASSWORD: The password is being reset on the server.
            1. PAUSED: The server is paused.
            1. REBOOT: The server is in a soft reboot state. A reboot command was passed to the operating system.
            1. REBUILD: The server is currently being rebuilt from an image.
            1. RESCUE: The server is in rescue mode.
            1. RESIZE: Server is performing the differential copy of data that changed during its initial copy. Server is down for this stage.
            1. REVERT_RESIZE: The resize or migration of a server failed for some reason. The destination server is being cleaned up and the original source server is restarting.
            1. SHELVED: The server is in shelved state. Depends on the shelve offload time, the server will be automatically shelved off loaded.
            1. SHELVED_OFFLOADED: The shelved server is offloaded (removed from the compute host) and it needs unshelved action to be used again.
            1. SHUTOFF: The server was powered down by the user, either through the OpenStack Compute API or from within the server. For example, the user issued a shutdown -h command from within the server. If the OpenStack Compute manager detects that the VM was powered down, it transitions the server to the SHUTOFF status.
            1. SOFT_DELETED: The server is marked as deleted but will remain in the cloud for some configurable amount of time. While soft-deleted, an authorized user can restore the server back to normal state. When the time expires, the server will be deleted permanently.
            1. SUSPENDED: The server is suspended, either by request or necessity. See the feature support matrix for supported compute drivers. When you suspend a server, its state is stored on disk, all memory is written to disk, and the server is stopped. Suspending a server is similar to placing a device in hibernation and its occupied resource will not be freed but rather kept for when the server is resumed. If an instance is infrequently used and the occupied resource needs to be freed to create other servers, it should be shelved.
            1. VERIFY_RESIZE: System is awaiting confirmation that the server is operational after a move or resize.
        1. Server status is calculated from vm_state and task_state, which are exposed to administrators:
            1. vm_state describes a VM’s current stable (not transition) state.
            1. task_state represents what is happening to the instance at the current moment.
        1. Server creation
            1. BUILD
                1. While the server is building there are several task state transitions that can occur:
                    1. scheduling: The request is being scheduled to a compute node.
                    1. networking: Setting up network interfaces asynchronously.
                    1. block_device_mapping: Preparing block devices (local disks, volumes).
                    1. spawning: Creating the guest in the hypervisor.
            1. ACTIVE
                1. The terminal state for a successfully built and running server.
            1. ERROR
                1. The progress of the request can be checked by performing a GET on /servers/{server_id}, which returns a progress attribute (from 0% to 100% complete).
                1. You can retrieve additional attributes by performing subsequent GET operations on the server.
        1. Server query
            1. There are two APIs for querying servers GET /servers and GET /servers/detail.
            1. Both of those APIs support filtering the query result by using query options.
            1. query options
                1. 